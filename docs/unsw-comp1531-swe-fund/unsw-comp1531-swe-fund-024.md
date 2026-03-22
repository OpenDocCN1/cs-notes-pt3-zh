# 024：身份验证 🔐

在本节课中，我们将要学习软件安全的基础知识，特别是身份验证和授权。我们将探讨如何安全地存储密码、使用哈希函数以及如何通过令牌机制保护用户会话。这些概念是完成项目第三阶段的关键。

## 概述：身份验证与授权

身份验证是验证用户身份的过程，例如输入用户名和密码。授权则是确定已验证用户拥有哪些访问权限的过程。虽然两者紧密相关，但本节课我们将主要聚焦于身份验证。

## 基本身份验证方法及其问题

上一节我们介绍了身份验证的基本概念。本节中我们来看看最常见的身份验证实现方法及其潜在的安全风险。

![](img/4a999000b3e5b67a409ca520302b7c81_1.png)

![](img/4a999000b3e5b67a409ca520302b7c81_3.png)

![](img/4a999000b3e5b67a409ca520302b7c81_4.png)

最常见的做法是：用户注册时，服务器存储其用户名和密码。当用户登录时，服务器将用户输入的密码与存储的密码进行比对。如果匹配，则验证通过。

![](img/4a999000b3e5b67a409ca520302b7c81_6.png)

![](img/4a999000b3e5b67a409ca520302b7c81_8.png)

![](img/4a999000b3e5b67a409ca520302b7c81_9.png)

以下是一个简化的代码示例：
```javascript
function register(email, password) {
    // 将 email 和 password 存储到数据对象中
    dataStore.users.push({ email, password });
    return { success: true };
}

![](img/4a999000b3e5b67a409ca520302b7c81_11.png)

![](img/4a999000b3e5b67a409ca520302b7c81_13.png)

function login(email, password) {
    const user = dataStore.users.find(u => u.email === email);
    if (user && user.password === password) {
        return { success: true };
    }
    return { success: false };
}
```

![](img/4a999000b3e5b67a409ca520302b7c81_15.png)

这种方法存在一个严重问题：密码以**明文**形式存储。如果攻击者获取了存储数据的文件（例如 `data.json`），他们就能直接看到所有用户的密码。在真实的软件系统中，这会造成巨大的安全风险。

![](img/4a999000b3e5b67a409ca520302b7c81_17.png)

![](img/4a999000b3e5b67a409ca520302b7c81_18.png)

![](img/4a999000b3e5b67a409ca520302b7c81_20.png)

![](img/4a999000b3e5b67a409ca520302b7c81_22.png)

![](img/4a999000b3e5b67a409ca520302b7c81_24.png)

## 加密与哈希：隐藏信息

![](img/4a999000b3e5b67a409ca520302b7c81_26.png)

既然不能存储明文密码，我们需要一种方法来“隐藏”密码，同时又能验证用户输入的正确性。这就引出了**加密**和**哈希**这两个核心概念。

![](img/4a999000b3e5b67a409ca520302b7c81_28.png)

![](img/4a999000b3e5b67a409ca520302b7c81_30.png)

![](img/4a999000b3e5b67a409ca520302b7c81_31.png)

两者都是将明文（如密码）转换为看似随机的字符串的过程。但关键区别在于：
*   **加密**是可逆的。存在一个“密钥”可以将加密后的数据恢复为原始明文。
*   **哈希**是**不可逆**的。它是一种单向函数，无法从哈希值反推出原始输入。

![](img/4a999000b3e5b67a409ca520302b7c81_33.png)

![](img/4a999000b3e5b67a409ca520302b7c81_34.png)

![](img/4a999000b3e5b67a409ca520302b7c81_35.png)

![](img/4a999000b3e5b67a409ca520302b7c81_37.png)

哈希函数就像一个“搅拌机”，输入任何内容，都会输出一个固定长度的、看似无规律的字符串。例如，输入 `hello` 可能会得到类似 `2cf24dba5fb0a30e...` 的哈希值。

对于密码存储，我们需要的正是**哈希**这种不可逆的特性。我们不需要知道用户的原始密码，只需要验证他们输入的密码是否正确。

![](img/4a999000b3e5b67a409ca520302b7c81_39.png)

![](img/4a999000b3e5b67a409ca520302b7c81_40.png)

## 使用哈希安全存储密码

![](img/4a999000b3e5b67a409ca520302b7c81_42.png)

![](img/4a999000b3e5b67a409ca520302b7c81_43.png)

![](img/4a999000b3e5b67a409ca520302b7c81_45.png)

![](img/4a999000b3e5b67a409ca520302b7c81_46.png)

![](img/4a999000b3e5b67a409ca520302b7c81_48.png)

理解了哈希的原理后，我们来看看如何将其应用于密码存储。

![](img/4a999000b3e5b67a409ca520302b7c81_50.png)

核心思想是：**存储密码的哈希值，而非密码本身**。

![](img/4a999000b3e5b67a409ca520302b7c81_52.png)

以下是更新后的流程：
1.  **注册时**：当用户设置密码时，服务器立即计算该密码的哈希值，并将哈希值（而非原始密码）与用户邮箱一起存储。
    ```javascript
    import { getHashOf } from './hashUtil';
    function register(email, password) {
        const hashedPassword = getHashOf(password); // 计算哈希
        dataStore.users.push({ email, password: hashedPassword }); // 存储哈希值
        return { success: true };
    }
    ```
2.  **登录时**：当用户尝试登录时，服务器对他们输入的密码进行**同样的哈希计算**，然后将得到的哈希值与之前存储的哈希值进行比对。
    ```javascript
    function login(email, password) {
        const user = dataStore.users.find(u => u.email === email);
        const inputHash = getHashOf(password); // 哈希用户输入的密码
        if (user && user.password === inputHash) { // 比对哈希值
            return { success: true };
        }
        return { success: false };
    }
    ```

这样，即使数据库泄露，攻击者也只能看到一堆哈希值，而无法直接获得用户的原始密码。

## 关于哈希与彩虹表的补充说明

虽然哈希是单向的，但攻击者仍可能使用“彩虹表”进行破解。彩虹表是一个预先计算好的、包含大量常见密码及其对应哈希值的数据库。如果用户密码很简单（如 `123456`），攻击者可以通过查表快速找到对应的原始密码。

因此，鼓励用户使用**长且复杂**的密码至关重要。密码的长度和复杂性会使得可能的组合数量呈指数级增长，从而让构建完整的彩虹表在物理上变得不可能。

## 令牌、会话与防篡改

在项目的第三阶段，除了哈希密码，还需要保护会话令牌。在之前的实现中，登录后返回的令牌可能只是一个简单的会话ID（如 `123`）。攻击者可能通过猜测或篡改这个ID来劫持其他用户的会话。

为了使令牌防篡改，我们可以采用签名机制：
1.  登录时，服务器不仅生成一个会话ID（如 `sessionId`），还使用一个只有服务器知道的**密钥**，与会话ID组合后计算一个哈希值（即签名）。
    ```javascript
    const sessionId = generateRandomId();
    const secret = 'my_server_secret';
    const sessionHash = getHashOf(sessionId + secret);
    const token = { sessionId, sessionHash }; // 返回给客户端
    ```
2.  客户端在后续请求中携带这个完整的 `token` 对象。
3.  服务器收到请求后，使用存储的**密钥**和收到的 `sessionId` 重新计算哈希值，并与客户端传来的 `sessionHash` 进行比对。如果匹配，说明令牌未被篡改。

这样，即使攻击者截获并修改了 `sessionId`，由于他不知道密钥，也无法生成正确的 `sessionHash`，因此篡改会被服务器发现。

## 在HTTP头中传递令牌

最后，我们需要改变令牌的传递方式。在之前的实现中，令牌可能通过URL查询参数（GET/DELETE请求）或请求体（POST/PUT请求）传递。

然而，URL查询参数在网络传输中通常是**不加密**的（明文），容易泄露。为了更安全，我们应该始终将令牌放在HTTP请求的**头部**中传递。

例如，在使用 `axios` 库时：
```javascript
// 将 token 放在请求头中，而不是查询参数或请求体里
axios.get('/api/channel/details', {
    headers: {
        'token': JSON.stringify(userToken) // token 是一个包含 sessionId 和 sessionHash 的对象
    }
});
```
HTTP头部信息在HTTPS连接中是加密的，这为令牌提供了更好的保护。

## 总结

本节课中我们一起学习了软件安全的基础知识，重点聚焦于身份验证。我们探讨了以下核心内容：
1.  **哈希密码**：使用不可逆的哈希函数存储密码，避免明文存储的风险。
2.  **令牌防篡改**：通过结合密钥对会话ID进行哈希签名，确保令牌的完整性，防止会话劫持。
3.  **安全传输**：将敏感令牌置于HTTP请求头部中进行加密传输，而非不安全的URL查询字符串。

![](img/4a999000b3e5b67a409ca520302b7c81_54.png)

![](img/4a999000b3e5b67a409ca520302b7c81_56.png)

这些实践是构建安全软件的基础，希望你能在项目第三阶段成功应用它们。