# 【全集 2025 附课件】马萨诸塞大学 分布式系统 中英字幕 p25 Lecture 25 - 分布式系统安全 -BV19BSYBuE4Y_p25-

![](img/e742897255c5827254e726d8a9432359_0.png)

Best。Okay so it's a couple minutes early but I'm going to start and let me just begin with announcements I'll send whatever I'm going to say also in an email so we have two things left there's a lablet and a homework that's due this week and then we have a final exam next week and then we'll be done with the course so just a couple things about the final exam it's on Tuesday at one o'clock and it's going to be in Marcuscus hall that's been on spire and on the class web page since the very first class and'll send a reminder about this final exam is two hours long there's a little bit more time than the midter and as I said previously we will only have lectures 13 through today's class on the final which is all the material since the midter okay typically we have had it comprehensive but then I decided this year just to simplify it a little bit so you don't have to worry about。

The first 12 classes that were already covered on the middleter okay just focus on the latter half I gave out a sample exam I gave out some review material so you can use that as a basis to study for the final okay and then we will have the lab grading done lab two that is not three we just came in right lab not La two excuse lab three half done。

Okay， so lab three， we will have it done by end of this week and have it to back to you before the final exam。

 if you have any questions， you can always submit regrets al right so the。

And then is there anything else you'll also get the lablet and the homework done too because we have all of this last minute stuff we'll get it all back to so let's start today's class is the last class of the semester is going to be on security and specifically of security intersects with distributed system okay so the thing that you want to keep in mind is because you now have a system where components of that system are interacting over a network that was the definition of a distributed system the any component of the system can not only be accessed by users of the system but adversaries outside the system because the system is accessible either or the internet or a network so what that means is while if you have a centralized application you could just run it on a machine the machine doesn't even have to。

We connected on the Internet distributed applications。

 you really need to think about securing your applications otherwise you will see that there are unauthorized access or or other issues that cope at least some of you saw this also as part of your cloud lablet or lab when you started AWS instances we saw that some of your instances got attacked because they had a public IP and then there are bots that are going and trying to attack every machine that appears on the internet so there's something we got to think about and take seriously so today well do a very quick overview of the issues and distributed system security some highlevel techniques that can be used and towards the end I'm talk a little bit about how security concepts can be used in distributed systems rather than making them secure used in the context of electronic currency and cryptocurrencies。

So that's what well do。 So let's start with essentially a little bit of a definition about what security and privacy means。

 So first thing is these are actually different concepts they sound similar but they are not they' related but different security essentially relates to things like unauthorized access to resources theyre trying to get access to data computing resources to which you do not have access to usually you can use this unauthorized access to steel data you could for example get access to a bank's computer or database and still sensitive credit card information that's an example of a security issue privacy is not the same as security privacy violations can occur without any security violations altogether privacy also relates to getting access to data that are user did not wish to share with you but you can do this without for example unauthorized access one example of a。

Pivacy violation is you have a mobile app running on your phone it's collecting location information because you gave it access now the user not the user。

 the developer of this app can use that location to do more targeted advertising or can see sensitive information like your phone is being seen in a doctor's office so then you went to the doctor you be sick or something like that right so that's an example of a privacy violation unintentionally some information got leaked without the user wanting it to be there's no security problem there but still some data got so so that's a difference between security and privacy that you should think about there's a lot of important privacy issues in the context of machine learning that I will not of course talk about but something you to you should know for example you can take a neural network and probe it and try to understand some characteristic of the training data that was used to train。

Right something that maybe the whoever trained the neural network did not intend to happen so so that's another example of a privacy violation similar to the mobile app example okay again no security but privacy but as for today's class is concerned we are only going to talk about security not privacy but so let's with that background start with security so I'll start with something very simple which is authentication authentication is a mechanism that allows a user or a system to prove another system who they are right so it basically。

Pvides the identity of a user or a system to another entity in that distributed system。

 So let's take a very simple example。 you get a phone call from your bank that says they're calling from the bank。

 they need to verify something and ask you for some sensitive information like maybe your ATM card number or a pin number of course you can't just trust somebody use calling you or the phone so you are verify their authenticity authenticate their identity right so so how would you know that a remote entity is who they claim to be that's our authentication problem so so youll go through a set of protocols to design an authentication protocol so first thing is if we will use the standard terminology that you use in security the two entities will be called Alice and Bob right so this could be computers this could be two users one of them could be a user another one is a computer we don't care from our perspective well just use these two entities Alice is。

To authenticate themselves to Bob So if Alice just sends the user name saying I'm Alice okay Bob cannot believe that that would be Alice because someone else in this case an intruder Trudy can also impersonate that message claim to be Alice right so you need more information or Bob to trust that Alice is who she claims to be right so so one of the things that you can do in a distributed system is to actually use the IP address or the machine where the packets are coming from as a way to authentic it so you can say if Alice in this case was a computer you can check is Alice actually the packets coming from the IP address of the machine's that's Alice's machine so you could do this but even this technique is vulnerable to what's called IP spoofing where you can send IP packets with a fake address so you cannot just believe because you got a packet or the internet from a。

A certain IP address that it originated there because you can spoof it in fact when we talked about web cluster scheduling I showed you an example where the backend replicas were spoofing the address of the frontend switch so that the user browser believed that the hTP response came from the same machine so that's commonly used both for good and bad purposes so if it's a bad purpose then you cannot believe that the machine is actually Alice's machine right so you will get to a typical thing where you will use a password so this is what we are familiar with you have a username and a password so Alice can send a packet box saying I'm Alice here is my password but if this text is going unencrupted over the network that's a problem because Rudy can intercept this packet extract the password and then you can essentially log into into the system claiming to be。

Alice so so when you have communication back and forth。

 even if your username and a secret password if this information is going unencrypted over a network that information is vulnerable to s Sy by adversary and they can get your password so there are protocols which no longer exist but you should know like FTP and Tnet that essentially use this type of technique to log in and they were unsecurure so did away with that use things like SSH and SSFTP which are more secure but we'll get to those so that's version3 that's not going to work so what well do instead is now use encryption for communication so we will essentially use some way to provide secret information that's only known to Alice and Bob so this is basically going to require that we use an encryption algorithm I will just talk about it very briefly as to what encryption is not go into the details but you need to at least have a highlel ID so an encryption。

Algorithm is a function that takes an input and it takes a key and it produces an output。

 which is the encrypted version of this。 So if you have a string。

 let's say hello world that's your unenryed text you have a key you feed it to this encryption function it will produce another string and the properties of the encryption function are given the encrypted string you should not be able to figure out what's the original message that was being sent and you essentially need to use the key and that encrypted message pass it through the same function to recover the original so you can essentially use this function as a way to encrypt your communication。

 This is called an encryption algorithm we will see some examples of this but for now just assume there's an encryption algorithm you don't really need to get into the details so all encryption algorithms need a key the key is the thing that you' are going to use to encrypt algorithm So the algorithm is going to be the same for all the users the way it will differ from。

One user to the other is they have a key that is not known to anyone else and there if you use using that key you can encrypt and the messages so in this case we will assume that there is a secret key which is known only to Alice and Bob we call it some key key。

So what Alice is going to do to authenticate herself is youll basically take the username which is I am Alice and encrypted using that encryption algorithm and the secret key so that basically gets you this is now the encrypted version of the message you are going to send it over the network Bob is going to take the encrypted message and so essentially the message that came the secret key that' is only known to the two of them and decrypted and you get I am Alice back and this allows you to now authenticate Alice because the key is only known to Alice and Bob so you know that that message could not have been sent by anyone。

Okay all right so that is a version of the authentication algorithm that uses encryption but this algorithm is actually vulnerable to what is called a playback attack so what an intruder can do is essentially capture this encrypted version of the message。

😊，The intruder does not have the ability to decrypt this message because the intruder does not know the secret key。

 but that is okay because all that the intruder truly has to do is take that encrypted message and send it back to Bob saying I am Alice and Bob will allow you to log in because Bob will decrypt the message and believe it came from Alice。

so encryption by itself didn't help us because this is now vulnerable to what' is called a playback attack where you are not you don't know the contents of the message。

 you cannot extract the contents of the message but you present the same message again to Bob and now you essentially are able to prove that you are honest。

Okay， so we added encryption that didn't work。 We added a password that didn't really work。

 So what should we do now Okay so here is where we will get to。

This notion of what is called a nounance so we will use our nos which are somewhat similar to onetime passwords but in a different way here than what you might be familiar with when you use the one-time password so what is a no so nounance is essentially once in a lifetime integer so essentially from our purposes is an integer but it's something that you generate for every session but once you generate you can never generate it again so it's a once in a lifetime integer that you will generate for the purposes of authentication in this case and you will never be generating it again for subsequent login or authentication so that's what we mean by no so it's basically an integer that's one time and you will never use it again so just a final authentication protocol Alice will send a message to Bob saying I'm Alice username right so that's an encrypted Bob is going to generate a one time non integer in and send it。

back to Alice and say prove that your are Alice with this integer now Alice is going to encrypt that Nouns previously you encrypted your username now you are encrypting the Nouns with the secret key and then you send that encrypted nouns back to Bob Bob will decrypt it and verify that the Nouns actually came back so now you have authenticated Alice。

Now this technique is not vulnerable to playback attack because all that the intruder can do is capture this encrypted version of a no。

 but if you try to log in again a new no is generator so this one is useless。

Because it's a one time use only。Is that clear what I just said here okay so you can use this notion of nonsense to and just use the same type of encryption idea from the previous slide to get away from playback attacks which are a problem if you use encryption。

Okay， yes， question。Okay the question is the first message which is the username saying I'm Alice we could just send a username is unencrypted what happens if that message is captured right so if some intruder captures that message they'll know the username for Alice but I cannot do anything with this information to authenticate themselves yes the username is known but how will you log in because if you say present the username to Bob Bob will send a new nuunnce you got to encrypted with the session a symmetric key that the intruder does not know so you cannot just use the username produced to perform authentication in this case。

Okay。You are the questions on the list。这什东。好。本据生定的。这个。Whats weather。对。

Okay question is is there a timeout and when the no is actually going to expire so in this case there is no such thing as a timeout this is a simple protocol we don't worry about how long each message takes to go and come back so you can take a while for the message to come back that's okay the main thing here is the nouns is now are going to be used again once its generatedrated for any subsequent attempts by this or any other user and then the second thing is the key that is being shared by Alice and Bob is only known to Alice and Bob right so those two so long as those two properties hold then this is fine right of course somebody breaks into a computer and steals your key all bets are off then that intruder can use the key to encrypt the mess so long as your key is secure and the nouns is never regenerated this protocol is。

Okay。Any other questions here Allright so that's not So now we will try to make this slightly different where we will use a different type of encryption algorithm which is called public key cryptography so this encryption algorithm uses two keys not one so typical encryption algorithm use a single key the same key is used for encryption and decryption so the encryption key and the decryption key or one and the same and they have to be known to both parties and then so long as you have that key you can either create an encrypted version of the message or given an encrypted version of the message you can use the key to decrypt the message in public key cryptography you have two keys not one so one key you can think of as an encryption key which is also called the private key the other is the decryption key also called the public key these two keys。

And we used to encrypt and decry really you don't have to call them encryption and decryption they are actually symmetric but there are two keys in this system okay and the way this is going to work is when a user creates a key this pair of key they will take one key and then say this is my private key I will not share it with anyone so that key is only known to that user the public key you can give to any user is supposed to be public okay so anyone can have that key。

It doesn't matter even if the intruder has that key so anyone can have a public key okay but the private key is only known to that user so that' is the assumption and now what you can do is if you encrypt something with the public key you can decrypt it with the private key but the reverse is also true because the symmetric if you encrypt something with a public key you can also decrypt it with the private key okay so it is a symmetric protocol but for now assume that private keys are used for encryption public keys are used for decryption just as an example so how will we change our previous protocol to do authentication we will assume now that Alice and Bob will have this pair of keys but the private key is only known to Alice because Alice is the one trying to do authentication the public key can be known to anyone but also known to Bob。

So Alice is going to send the same message I Alice username goes Bob is going to say heres a nouns prove that your Alice okay so Alice will take the private key encrypt the Nouns and send it to Bob now Bob will use the Alice's public key and decrypt that message and the nouns will be extracted and then you will know that only Alice production and send this because no one else has Alice's private key so only Alice can encrypt it。

Now someone else intruder can also decryb this message because the message public is known。

 but that's not going to do anything because you are just trying to do authentication in this case from authentication purposes the fact that you could decry Alice's message does not provide any value to an intruder so you can still authenticate。

Is this clear？Any questions here so so this is a more modern way of doing authentication where you will essentially get a one time nonsense and then you will use that to encrypt and sign back。

And many authenticator apps that give you I think the one that UMass uses gives you an integer once in a while。

 if you enter that integer is doing something like this not exactly this is but something like because there its a two digit integer so it's not a once in a life you only have 99 of them。

Right。All right so that's authentication but here are some more problems with this approach so the problem here is how should Alice convey her public key in a secure manner to Bob because all of this assumes that Bob has somehow gotten hold of Alice's public key。

Right， so。So how did Bob get that information in the first place and if you don't do that well this is called distributing your key or key distribution you can essentially break this protocol even though it's secure from every other aspect key distribution can be a problem so here's a issue that you could think about so so let's assume there's Alice communicating with Bob and theres Trudy the intruder sitting in the middle and we'll assume that Trudy can intercept messages that are going back and forth whether Trudy can decrypt messages is different problem at least can intercept messages okay so here's how things might work so。

Rrudy can impersonate Alice in the following， Rudy can send a message to Bob saying I am Alice。Okay。

 so Bob is going to send a no saying prove that you are Alice。Now。

What Trudy is going to do is the Trudy is going to essentially send an encrypted version of the Nos。

 but Trudy does not have Alice's private key in this case so Trudy can just use her private key and send it so this is now an incorrect encryption because this is not actually use Alice private key now Bob in order to decrypt it as first got to gut get get。

Tlysislysis public key so that has to be retrieved so maybe you can think of a way that Bob is sending a message to Alice and send me your public key。

which Trudy can intercept and Trudy can respond pretending to be is saying here is my public key and send her public key instead。

Okay now Alice now Bob does not know that this message actually came from Trudy you can do IP spoing and send that message and believes that this is Alice is publicly so Bob is going to use incorrect key to decrypt that message and get the nuuns and believe that it is actually Alice。

This is in the presence of a state of the art encryption algorithm which is public key cryptography you can still break it this is called a man in the middle or person in the middle attack where the intruder is sitting in between and causing problems。

😊，Now this does not mean that the encryption algorithm is the problem encryption algorithm is very secure the problem is with key distribution you do not have a secure way to distribute your key and if an intruder can send fake keys to a computer or another user then all bets are off right so you want to make sure the keys that are being shared between two pairs are actually distributed in a secure so so what this is saying is。

😊，The encryption algorithm is only as good as the key distribution algorithm。

 you can have very secure encryption algorithm but if you have a bad or a lousy way to distribute keys it is not going to help。

😊，so then another example， if you want to think is maybe you think about you have a you put a secure lock on your front door。

 but you can put the key under the mat。Okay not going to help if somebody gets your key they can break open the lock。

 they not to break the lock it is the same problem our key is not distribution it not secure so we want to make sure that part is secure as well。

Right， okay。Let's assume you know how to do key distribution I'll get back to that in a few slides but for now assume it's secure what can we do with some of these things so let's talk about digital signatures as an application of all of what we just talked about so in digital signatures you are trying to sign a document but rather than using an actual paper copy and using a pen you are going to essentially sign it using a computer okay we are going to put a digital signature how is that going to work so the goals we want for any digital signature algorithm are that the sender cannot claim that they did not sign a message if they actually did。

If you signed a message，You shouldn be able to claim you did not sign it because there will be a way to verify that you signed。

And this you cannot claim you didn't sign it and the receiver should not be able to fake somebody's signature as well。

And so you want these two properties you want to make sure that if you sign it you you cannot later on claim you didn't sign it and and then someone else cannot use your signature right so if you are these two properties you get a digital signature algorithm okay here's how it's going to work so lets say that Alice wants to sign a document or a message it doesn't matter what the message is doesn't matter what the document is just assume it's a string。

OkayIt's a string of bytes that's any arbitrary document can be represented as a string of bys。

 so we will assume that Alice wants to。Sign the message so what Alice is going to do is she will take the document or the message M and she will simply encrypt it with her private key。

And this encrypted version of the document can also serve as a signed version of the document because the public key is known to everyone because that is public you can put it on your web page if you so wish you can decrypt the document。

And extract the original content but you can also verify that only Alice could have signed this document because the private key is only known to Alice so only Alice can generate the encrypted version of the document。

No one else can。The fact that only you can generate it can also serve as a signature for this protocol。

Okay so one way to sign a document is to simply generate a public and a private key pair use the private key to encrypt a message and then say that the encrypted version of the message is the signed version of the document or the message and then it can be verified someone you cannot claim you did not sign it because only you could have encrypted it no one else can for this because your private key is only known to use only you can construct this version so though both of those properties will be addressed in this case。

Is that clear so this is a very simple way to have digital signatures。

 but it is not an efficient way。😊，In fact， it is a very inefficient way because public and private keys are very large in size okay they are large because they are they have to be secure so the larger the key the more secure it is okay but the larger the key the more computationally intensive the algorithm is to generate the encrypted dose so this is 100 page document you signing is。

😊，Your machine is going to take a while to generate the encrypted a version because it is taking a very secure algorithm and trying to encrypt that do。

😊，So， it is not very efficient to encrypt and decrypt the large documents with public and private keys as signatures。

😊，So you want to get this type of property but in a more computationally efficient manner。

That clear what I just said， any questions that okay， so what can we do？Anyone have any thoughts？Yes。

Okay， you could only append a small part and only that part is signed。

 you kind of are on the right track so you don't want sign the full document。

because that is going to become traditionally efficient inefficient rather。

 so you want to sign something smaller and sign it as the signature with the document right that so what is it that you can use that smaller you can use something called a message digest what is a message digest message digest simply a hash。

think of a hashing function what does hashing function do takes and arbitrary length string you will take that hashing function you feed the string it generates a fixed length hash so you can get any arbitrary lens string。

Imput it into the aing function， you get a fixed length， a smaller string。

that is our property of a hashing function now the hashing function should have low probability of a collision which means two strings should not produce the same hash otherwise we are going to have problems but good hashing functions already have that property。

So， here is what we will do we will take a hashing function edge to help us with making the digital signature more efficient so we will take the arbitrary lens string m and we will generate a hash。

😊， so that's a fixed length string much smaller than the original document which could be abitrly。

And then Alice is going to essentially encrypt the hash， not the original message。

 but the hash of the message。The hash of the message is actual signature。😊。

In this case so you have the document m and you have the signature which is the hash of your message and you can take these two pairs and present it to someone they can verify that you sign the message because they can regenerate the hash hashing function is supposed to be public so take m which is the original message generate the hash okay and then you can use the public key to decrypt this hash and verify that the two are the same。

Then you know that Alice signed this message and Alice cannot claim he didn't sign it nor can anyone else generate this encrypted version of the hash。

This is going to be far more efficient because hasing is a much cheaper operation than encryption。

 such as the hasing function and then since you are going to encrypt a much smaller string okay the computational efficiency is bounded use not that arbitrary lensing it can take arbitrary amounts of time。

😊，Yes。Yes， question is does this mean that anyone who has Alice's public key can verify that Alice assigned it that is in fact true because the public is known to anyone you can verify that Alice signed it because if you have Alice is public key you can verify that you sign not very different from if you actually you write your signature so long its legible somebody can say that looks like your name there so something like that。

That not supposed signature nature， not secret。You can verify okay so here are two properties of any good hashing function and also required for ensuring that this digital signature algorithm works which is given a hash function edge。

 you should not be able to find a message or construct a message that essentially gives you that hash function。

RightSo if I just give you an arbitrary hash function you shouldn't be able to generate some message that gives you that hash function because if I give you some encrypted hash and I could then take the hash and say here's another document that gives me the same hash now you sign that document as well that's a problem so you shouldn't be able to take a hash hash value and construct a actual string that gives you that hash so you shouldn't be able to reverse the hash function in another way and the second thing is collision probability should be look you shouldn't have two strings that generate the same hash because then you have the same problem if you sign one document then you can claim that you also sign another document because it generated the same hash because they collide。

Right so so long as and these are general properties of hassh functions and nothing to do with message digests or。

digitaligital signatures， but they are good properties to have for the hashing function to work with hasing functions are typically not inverable and they also tend to a low collision probability these are also called cryptographic hash function not every hash function will have that property like mod is a hash function modern that's not going to have this property will have lots of collision every n integers will give you the same hash for example right but yes in cryptographic hash functions will have this property and then you can use them for digital。

OkayAll right。What kinds of cryptographic hash function should we used we not get into details of how to construct this hash function but I'm going to mention some of them yes for a very long time there was a hash function called MD5 which just an acronym message digest 5 which was used to perform all kinds of hashing was used in digital signatures and so on。

 but after a while it became easy to break it which means you could invert it。

And then if once you can invert hash function is not secure anymore so they decided not to use it。

 but 10，15 years ago when I taught this class they said that's the one to use for digital signatures but now that's not the one to use。

 you should now use a more secure hash function， once there's a family of them called Sha hash function。

 Shah just means secure hash algorithm。There's different families with different hash lengths so that's the output length so Shah 1 produces 160 bit Shah2 and more has basically 256 bit5 12 bit 124 bits and so on okay so this was designed by NISistT and NSA is still state of the art practically any encryption algorithm that needs hashing will use a Shah hash so that is the one that you should use if you are using things like digital signatures or any other thing that requires hasing。

Is this there any questions we won't get into details but it you should all of these modern hash function will have these two properties shouldn be able to invert it collision probability should be。

Okay。All right， so with that。Let me talk about one more thing and then we'll get to secure email。

 So essentially let's talk now about how are you going to do key exchange because I said there has to be secure way to exchange keys otherwise we have all of these problems where if you send keys unenrypted somebody can intruder can get hold of it and you have trouble in terms of actually encryption So how do you distribute keys in a secure manner so that's that's a problem in itself that's called key exchange or key distribution so you'll see two ways to do this in one approach will use a trusted third party that trusted third party will actually generate the key and we'll give it to Alice and Bob in a secure manner then Alice and Bob can communicate with that secure so we'll use a trusted third party which will be called the key distribution center and then'll see another algorithm which decentralize no third parties you can essentially。

Generate keys and exchange it in a secure manner。 Okay， So two ways to do key exchange。So here。

The one that uses the th or third party you have Alice on the left Bob on the right the key distribution center which is called the KDC sitting in the middle protocol is very simple Alice is going to send a message to the key distribution center saying I'm Alice I want to communicate with Bob generate a key。

The key distribution center is going to generate a secret key which is only valid for one session between Alice and Bob。

 which we call k I mean AB which means is a key for Alice and Bob and。

That key is going to be sent to Alice in an encrypted manner so the assumption behind key distribution center is that Alice has already a secret key that is shared with the key distribution center that can use for secure communication Bob as a secret key thats only to the key distribution center and Bob that can be used for communication so long as you have this you can have bootstrap communication between any two pairs of users because they don't need to have a predefined sex secret key so long as you have a secret key that you share with the KDc that KDC can generate a secret key for any two pairs in the system to communicate with one that's the assumption so so you take this key KabB that was generated by the KDc you encrypted with the secret key that Alice and the KDC share and send it you can do the same thing and send that to Bob is the same key now Alice and Bob have a key that they can use to communicate the case you are using the KDC to。

Trap your secure communication。I that clear， yes。Okay question is is there a protocol to share a key between Alice and KDC and Bob and KDC So in this case that's going to be a recur recursive problem right so so the way well assume is that youre to bootstrap it in a secure manner which is not an electronic means。

 for example， you actually physically go into the KDC office they generate a key they install it on your computer youre done you're not using a network to communicate so you'll assume there's an offline means to share that key once you have that youre done right that that's the assumption here because there is no secure way because otherwise you mean we'll see another protocol which you can do away with KDC you could use that of course to bootstrap as well。

This here there is a variant of this where which I didn't show here where the key is sent by Alice to Bob but this is kind of already showing the main idea so I will not go into that variant instead what Ill show is a technique that does away with the trusted third party so we are going to use。

Public key cryptography for Alice and Bob to generate a session key。

You could say why do you need a session key if you already have public and private keys couldn't we just use the public and private keys to communicate why can't Alice just encrypt every message with the private key and then public bo can decrypt that message why do we need a separate key so thats a question we should ask and the answer is no different from what we had in the case of digital signatures if you use public cryptography is very expensive the keys are very large in size okay so that' is going to make your encryption and decryption process really slow so what you would rather do is use that secure key。

Seett of keys to generate a somewhat smaller key that is used for just one session which will allow the encryption algorithm to be still very secure but not very inefficient so you want to essentially use public cryptography to bootstrap so so here is how it is going to work Alice is going to send a message to Bob saying I'm Alice here is a nonce。

 generate a session key and Alice is going to take Bob's public key。

And encrypt that message the public keys can be used for encryption as well as decryption so once you are encrypted only Bob can decrypt this message because you need the other key to decrypt it that key is only known to Bob so no one else can get the hold of this noun because it is now encrypted with Bob's public key but Bob can decrypt this message and say this message came from Alice here is a nonce that came with it Bob will generate any arbitrary session key doesn't matter which is generate a long key it's a big integer what you will do is you will send the nounnce you will send。

Essentially， the。A new sorry the old nouns will generate a new nouns and the session key this time Bob will encrypted with LS public because thats also known and that message can only be decrypted by Alice because no one knows else knows the private so Alice will get this message extract the content say that's the nouns that I send so that's the key that was meant for this session and you will get this nounnce you send that nouns back so that Bob knows that its like an acknowledgement saying you got the message and nonces。

Now you bootstrap this session with a specific session key。

 you can then use that key to use a symmetric encryption algorithm。Then which will be more efficient。

So this is a way you can securely distribute keys。A you any questions here？Yes。W something。Yes。

 good question and we will talk about that as well so this requires that the public keys were securely distributed in the first place right how did Bob and Alice get to know each others public key。

😊，so that's a question we got to ask and that we need an answer to that otherwise you will say send an unenrypted message to Bobs and give me your public key that can be intercepted and someone else can send their public key。

Naming to be Bob San， you are back to the man in the middle attack。All right。

 so what shall we do here， so we will go back。To a trusted server for secure distribution of public keys not for distributing session keys but for secure distribution of public keys but the server is not going to be in the loop for every message exchange instead it is going to be trusted for a different reason what it is going to do is it is going to take any public key and it is going to sign that public key saying I certify that that is actually Alice Alice's public key this is called a certificate。

If you have actually gone to any SSL browser you will see that there is a log symbol that appears you click on that lock you get a certificate so that certificate essentially is a public key that is signed by a trusted third party so you can actually believe that it's somebody's public key you don't just get a number and say that is Alice key somebody is actually attest to that Alice's public key and you believe that because you actually trust that whoever signed that key so this trusted server is going to be called a certification authority it does the authority to generate public keys that are signed so that when theyre presented you can actually decrypted and verify that that's actually signed so I believe that that's the right public key I don't get any public and believe it's somebody else' is public so we now use this trusted third party to essentially ensure that we will believe that somebody's public key so now we don't need any secure algorithm you can just freely sign your public key unenrypted it' not。

Anin sign， but you just send it and then the other first party can actually verify that it was signed by that certification authority。

 they will believe it。😊，So this is how a modern systems will look so heres what is going to happen The first thing is you will again need to bootstrap this certification algorithm by storing the certification authorities publicly on every system。

Yeah， because you have to verify the signature。And the way this is done is like every browser is going to come with 00 different predefined certification authorities that are built into the browser。

 what that means is the public key of all of those trusted certification authorities are already pre deployedeployed on your system。

Okay so so we basically don't have a protocol to share the certification authorities public keys that are actually stored in popular applications like browser or any encryption algorithm will have certification authority keys stored in that in fact if you go into a browser settings and go into securities you' will see a list of certification authorities that are known to your browser your browser and only trust those certification authority signature if some strange signature shows it will throw a certification warning saying I don't know sign this I'm not going to trust it。

Okay so here so so we will now assume that Alice and Bob have the certification authorities public key okay now Alice will go to the certification authority say generate a public key for me sign it so you will get that public key you will get a signature that is called your certificate you will say this is Alice this is Alice's public key here has a signature to verify which means you got a hash and you put a signature that you sign。

😊，So the way now if somebody presents your certificate saying I Alice here is the public key first youve got to verify that it is correct so you will take the trusted certification authorities key because now and then you will verify the signature the signature is signed with the private key that is only known to the certification authority you are the public key you will generate the hash the same digital signature algorithm you will verify that that that's a valid private key not somebody else's private so now you know how to get somebody's public key secure so if you do that then you can go back and make this part secure。

And because this assumed that you had Alice and Bob's public keys。

 how will you do it Alice will just present a certificate to Bob saying here is my certificate it has my public key in it use this to for any。

Communication and Bob will do the same and we are done。

This is what browsers do as well when they actually connect to a server。

 the server sends its certificate to verify that that server is actually the website you're going to not some bogus server that' is trying to pretend to be some other website。

Okay。Yes。How does the certification authority get public keys for new websites。

 so essentially you have to go and request a certificate。

And the certification authority is supposed to verify that you can't just show up and say Im somebody else give me a public key for that somebody they're supposed to verify that you are who you claim to be so typically if you're a user you are to provide a passport or some form of identity before they would issue one for for an actual user for computers they use other techniques。

And so on so if you want a certificate on a domain let's say UMass or ED needs a certificate so that the website can claim that they are so you are to essentially show that you own the domain and theyll only issue it to the domain owner you cant just show up and say give me a certificate for UMass and then you can put up a website claiming to be the UMass web server so they are supposed to verify this and so that's a physical process it' is not a electronic process。

That clear。Okay， so that gets us to certificates。We'll talk about a few things and we'll get to things like secure email so security is much more than what I covered so far it's a really complicated problem because all kinds of security issues that you to deal with only done very simple things like authentication and use of encryption to sign certificates and exchange keys but there are lot more problems you have to deal with so typical enterprises have lots of systems in place to ensure security of different aspects of the distributed system so you might have things like firewall that protect what traffic can go in and out you have special types of firewalls that are called deep inspect packet inspection or DPI firewalls that look inside encrypted packets to see if there are matching viruses in them and so on there are virus and email scanners make sure attachments that are coming on email don't have viruses in them you can have network level security where you have。

F traffic is encrypted your passwords to get ontofi traffics。

 you can have VPNs to communicate from external services and all of the other things I talked about certificates and SSL we talk about in just a second so multiple aspects and that thing the list goes on and on you will have websites that are secure you can have one time passwords to do authentication two factor authentication have become very common it uses some of the ideas we talked about but not all of them what we talked about are more secure versions than some of what done here。

 but these are pretty good as well and so on so we will not have time to go into all of this but I just wanted you to get a flavor of all the different things that have been in place to secure a network and systems but I'll talk about one thing which is what is a firewall with one picture so there's a picture of a network firewall what is a firewall supposed to do a firewall sit between。

An internal network and an out external network and all of the network packets have that are going out go through the firewall all the incoming packets also have to go through the firewall so here is on one side is our internal network so this is a machine thats sitting here on the other side is the external network every packet from any machine on this network has to go through the firewall to get out to the internet every packet that' is coming from the internet to any machine inside the network has to go through the firewall so essentially we have now one box that controlling all the traffic that is going in and out。

So what can we do once we have this capability， we can essentially add。

Add what are called rules to this firewall that tell us what is allowed and what is disallowed so the firewall can control what traffic is allowed and disallowed both on both direction and this is done by specifying rules rules will be basically some way to tell the firewall saying if the packet came from this type of machine and is going to this other type of machine either allow it or disallow it so they are called allow deny rules so they also called packet filter so every time a packet arrives to go out it has to essentially the firewall will check it look at the source address it look at a destination address and'll say is there a rule that matches this and you will find some rules because it always a default rule and that rule will tell you is it allow or deny it says allow the packet will be let out if deny then you will drop it will essentially not allow that same thing for a traffic that's coming in and the packet arrives it has to match a rule for。

To be let in otherwise the firewall will simply drop it so the default for incoming packets is unless it was an session that started from the inside just drop that packet so the firewalls will not allow arbitrary traffic to come into your but the default is inside traffic can go out unless you added other rules to deny certain things。

So this is a popular mechanism that is in place if you have let us say a home wfi router that has a built in firewall they are doing the same thing it came with some default rules or those was default rules work but you can add your own rules to do other things if you want。

That so there's something you should know because there's some things that you will actually find in your home networks and so on as well。

 but they're also using enterprise networks to do more sophisticated things。

You can do a lot more with firewalls than what I just talked about。

 you can actually look inside the packet， you can do forwarding all kinds of other things。

 but this is by and large what a firewall will do for you and provide you with some degree of protection。

All right so I talked about all this so I'll skip this and access control let's talk about secure email so we have already talked about several different concepts okay so let's try to put it together to make an application we are all familiar with Se you know email right。

My default email is not secure you' are just writing some email sending it out， nothing is encrypted。

That your email is going unencrypted that's why you get spam because you can't verify who sent it what came and so on so can we actually make email more secure so what does that even mean what requirements do you want on our email so here's one set of requirements we can say we want secrecy secrecy means if I send an email to a friend only they should be able to read the content not somebody who intercepts my message right now if you intercept an email in transit you will read its content right so you want to make it secret。

You want to authenticate the sender and the receiver you want to make sure if I receive an email I can verify it to came from whoever is in the from address and vice versea if I send an email to someone I want to ensure that only the person named in the two address can not any arbitrary person so if essentially you want to do sender and receiver authentication and you want something called message integrity it means that no one altered that message in transit that you didn't actually change the contents of the message and sent。

So if you have those four properties you can essentially get secure email and whatever I just talked about in the past hour actually has all of the elements we need to build this so I will show you how we are going to build secure email so secrecy。

😊，How will we do secrecy， we want to encrypt our contents of our email message。

We already know something about encryption now what are we going to do we could essentially take public keys and private keys to encrypt our messages right so I can just say I will take my private key encrypt every message I will present my certificate which has a public key and you can verify right so you can do things like this but that is not very efficient so we will use something better。

we will use symmetric keys so what we will do is for every email Alice wants to send to Bob Alice will generate a symmetric keyK Alice will encrypt the message with that symmetric keyK so now I encrypted version of my email so I am going to take the key itself and I am going to encrypt it with my。

My my private key and I'm going to send this over， sorry， not my private Bob's public key。

So you will take Bob's public key and you will encrypt the session key only Bob can extract that key so you will send the encrypted version of the key and the encrypted version of the message。

so now I took the message I encrypted with the session key I took the session key。

 I took Bob's public key and encrypted it so only Bob can now extract the key because only Bob has the private key and once you extract the key you can decrypt the message。

OkaySo we just use simple encryption。And we essentially made got the first property。It just seccy。

Now， this does not give us。Other properties， so we will basically not be able to just use this to get all of those properties。

 but we got the first one。But let's try to do other ones as well。

So in know how to do secrecy can we do authentication can Bob figure out this message came from Alice if I just get an encrypted message with a key in my using my public key。

 I don't know it came from Alice。😊，Anyone else can generate this a message like this and claim that it came from Alice because nothing that Alice has that's in that message how do we ensure that the message came from Alice okay so this is going to require us to sign the message this message was not signed。

The way you prove that you are sending something is user a digital signature so let' us do a digital signature version of email but will leave a secrecy aside for just a second okay so IS will use a hashing function on the message and get the hash which would be a Sha function then you will create a digital signature of that hash。

Same thing we talked about so you take a message， generate a hash to sign the hash and then I send the message and I send the hash to Bob Bob can verify that Alice assigned the message at least I know it came from Alice。

The message here is not encrypted， so we are not getting secrecy here。

 but we are able to know that you got the message from Alice。😊，The previous one was encrypted。

 but we couldn't verify it came from Alice， this one we know came from Alice was not encrypted。

And so this got us authentication and integrity you can put both of these together and we will get all of our properties right so this is our full secure email protocol we will take a message am arbitrary lens string that you want to send Alice understandstein to Bob construct a hash。

え。S大。You signed it with your private key so you can verify it then I take the message and the sign signature and I make a new message M prime。

so I took the message I took the signature I make a new message M prime now I do the secrecy but I compute key key I basically encrypt m prime then I have to send that key securely so Ill take Bob's public key Ill encrypt the message and then I take the encrypted version of M prime and the encrypted version of the key。

 send it over so Bob can extract the key， decrypt the message verify the signature and you are done。

Right， so although we had very simple building blocks。

 you can see that you can put them together to get some。

Nfty techniques I mean none of this is actually done in standard email。

 but male clients will support this if you actually go get signal certificates and so on you can encrypt sign and what。

Is this dear？Any questions here？O。Allright so I'm going to talk about SSL and then we'll get hopefully to some digital currency concepts as well so let me speak a little bit about how your browser sets up an HttPS connection to the server you already know HtTP works you use that in your clients and servers but none of your traffic in your lab was actually encrypted that's not how modern browsers work all the traffic its HtTP is actually encrypted between the between the browser and the server so here is how it will work so the browser will first send a message to the server and HtTP message saying that I can support SSL which is called secure sockets layer this is what is used to encrypt your htTP communication and the server will essentially send another message back saying yes it supports encryption first you order to make sure that both the client and the server support encryption and the server are more important。

You'll send it certificate and this is my public key。

the browser is supposed to extract from that public key the identity and verify that the server is actually leg its not some random server you connected to apoofing an identity for a different server so you are basically going to get the certification authority private can and verify that certificate the browser will do it so once you are done this here you use your list of Cs to verify this then the browser will generate a PK it's a section key will encrypt that with the server's public key that came in the certificate and send that to the server as' a future message will be encrypted here is a session key。

And then the browse， the server can extract that key because it it' is sent with it an encrypted version of it is sent with its public key so you can extract it and send the key back and say future messages will be encrypted so now you just exchange the session key and you can use that to bootstrap communication。

Not very different from what we talked about earlier。

 but this is explicitly using certificates first you exchange your certificate and then you use that to bootstrap position。

So this is what will happen in your browser when you set up a HtTPS connection STtTPS simply means HtTP running on SSL you still stand regular hTP messages but the SSL layer will use that key to encrypt all the communication at the other end decrypted but at the application level you still get unencrypted htTP messages but in transit everything is going encrypted。

Is that clear， okay。All right， so one last thing and then they will wrap up so we'll talk about electronic payments and then we'll see how we can use some of these ideas to make some versions of secure currencies Okay so the first thing is how payment systems work So this is nothing。

To a distributed system these are just regular payment systems so if you're using cash to for your transactions the way this works is you as a payer will then get some money from the bank youll go and buy something you'll give cash and then the merchant can then deposit that money into their bank but when you use cash you get an important property which is anonymity you don't actually reveal your identity cash transactions are anonymous you go into store you pay something with cash they don't know who you are right at least not from your cash。

So that's a property he'll come back。You can also use checks to make payment so that's you are familiar with that your bare bank issues。

 your checkbook， you go as a payer， you write a check， the payer。

 the merchant will then present your check to the bank。 the bank。

 your bank and the merchants bank will run what's called a settlement process they will verify the check will verify the signature and then payment will go from the from your account to the merchant account there's now a settlement process involved between two banks for the transaction to takePrevious the banks were not involved now the banks are involved same is true for credit card transaction so you will essentially the bank will give you credit card or some other credit card is sure give a credit card。

 you present that to the pay the pay as to now run a separate protocol to validate that transaction that's not shown here you can go to mastercard and Nia network to validate it but as you make' validate it payment goes to the pay the payee will basically talk to your bank and when you pay the。

Pay your bills， essentially money will get transferred to whoever is transaction went。So again。

 there is a settlement process that's involved the important thing is。

If when you use check and you use credit cards， the anonymity part is gone because you are giving information about yourself。

 whether it's on your check with your checking account or information or your credit card typically will have your name attached to it and so on。

So you can now think about constructing electronic versions of this payment process by preserving some of these properties so that gets us to。

Their first protocol， which is electronic cash is not a real protocol。

 but I'm just going to illustrate to you how some of the anonymity of cash can be reserved in an electronic question so so here is how you can essentially construct an electronic cash so let's say you are the payer you want to generate digital coin for $1 you essentially generate a coin or you will ask a system to generate a coin for you but to make it real youre going to go to your bank and essentially ask the bank to sign it so that when you present this coin to someone they believe that is an actual $1 dollar electronic coin not something fake that you are present so you want a bank to verify or not verify to sign this thing yes this is $1 that you can present and if you present this coin to me I'll give you a dollar so you want the bank to sign it。

 but if the bank is if let's say the coin has a sequence number on it。And you sign it。

 the bank has a record of it。that they issued your coin$1 coin with this number and when you spend it they know that you spend it so it can be traced back to you as cash cannot be traced back to you so if you want the anonymity property what you are going to do is you are going to run a blinding process what is a blinding process think about this coin you put it into an envelope so that the sequence number is hidden and you ask the bank to sign that envelope。

not sign the coin itself so that whoever gets it says that this is actually signed by the bank so I should trust what's inside it so you will basically blind the coin you will essentially send the blinded coin which will be signed by the bank the bank will then sign that signature and then you can unbind it because of the bank signature and a $1 digital coin。

So that you can then go and give it to merchant the merchant will have to validate that it is a valid $1 coin by going to the bank and verifying the validity the signature is not enough to validate it because you can do things like double spending and so on right so so you will verify the wide and so long as the valid coin you accept。

So this is a form of an electronic cash protocol that was developed many years ago。

 it uses very simple things like signatures to get the job done but never really took off。

RightInstead we have cryptocurrencies or all the other things。

 but but this requires a trusted entity in this case is a bank that is signing something that everybody believes it has some properties of physical cash so you can actually。

Spend something without it being traced back。Okay so that didn't really go anywhere what is actually used widely are cryptocurrencies of which Bitcoin is one example Bitcoin uses many different ideas that we have used in this class its a peer to peer protocol decentralized not trusted third party involved you don't have a bank certifying anything there's an open source cryptographic protocol Bitcoin has its own ways by which it generates currency to begin with there are entities in the bit system。

Called miners that are essentially going to be able to generate coins。Yeah。

 so and there's a rate at which you can generate so miners are processes or computers in the system that serve multiple。

That's a multiple uses A they can generate currency so you can have more currency in the system over time but B they'll play a useful role in the system to validate transaction because this is peer to peer you are to keep track of who is paying whoop you are to say that this was transferred from this entity to the entity now owned by this other entity because if you just present a bit to someone how do they know you own it right there has to be a way to track it back and say you are the owner so you are allowed to spend it to begin with but the Bitcoin is just the number at the end of the day if you just present a Bitcoin identity then you need to be validated so you are to essentially be validated the way it's validated is there is essentially a large ledger that's keeping track of all the transactions in the system and the miners are the ones that are actually ensuring validate of all the transactions in the ledger so essentially as part of understanding bitcoin。

We have to understand what is a distributed transaction ledger， which also you not talked about。

 so we will essentially。Talk a little bit about this notion of a blockchain a blockchain is essentially a distributed ledger a distributed ledger is a distributed database but in this database there are two different properties that are different from a standard database this is a database where all records are public。

All the data in the database is completely public nothing secret in there and moreover it essentially lists every transaction that has happened in the bitco system so you can track who is transfer how much money to whom who owns what coins and so on that's all public except that the identities of who is not necessarily public because identities are simply public key they don't have to be tied to a particular person you can just have public key that's a number so you can't actually go back and see who that is so long as you have that key you can basically have access to all your current but you don't have to tell the system who you actually are but as a public key associated with with all of these coins and so and there is blockchains are much broader use than。

Cryptocurrencies they are used for stock transactions they're used for land transactions when you buy and sell land you can record them in a public ledger marriage records smart contract there are all kinds of use cases for blockchains where this type of property is important where the information is public right so all real estate information at least in this country all land records are public so you know who owns a certain piece of land so you can put that in a blockchain it can be cryptographically signed you can transfer it and you can essentially do all of those things that blockchain allows you to so。

We will now actually use this in the context of cryptocurrencies so essentially in this case we want to sign every transaction with the key and insert it in the ledger and then essentially we will have a block of this transaction well put it in the ledger so that is done with。

bititcoin P2 B protocol so it does a peer to peer protocol but there are special nodes called miners every time you want to add a block which is a set of records to the ledger you will ask the miner can validate this block and add it to the ledger so the miners have to now run a consensus protocol because you can just arbitrarily add whatever you want then the ledger will have。

Bad information because the mine one of the miners is malicious it can insert bad information so you always have to run a distributed consensus protocol before you agree on okay we will all agree that these this is the next record to add to our ledger furthermore this consensus protocol has to have more secure properties than Paxos because Paxos does not deal with Byzantine faults it can deal with crash faults but here some miners can be malicious so you want to ensure that even if some fraction of the miners are Byzantine faulty they are trying to do arbitrarily bad things the state of the ledger is always preserved it cannot be corrupted by a fraction of the mine and this goes back to our BF properties where you need3 f plus one miners to tolerate f fault0 miners。

So if you have Byzantine fault you will need a large number of miners to ensure that if some fraction of them go rogue or become 40 the ledger integrity is still not violated so we will use something which we have not looked at in this class which is called Byzantine consensus it is distributed all consensus protocols are distributed but this one does Byzantine it can add Byzantine fault we didn't look at that but assume that such a protocol exists so essentially what is going to happen is it a big picture but for what essentially happens is you generate some entries you want to add to the ledger you send it to the mining networks so this is a set of nodes that are sitting and running consensus and the one that actually essentially wins that consensus essentially gets to add or the set of them get to add it to the ledger and then for doing all of that work you will be rewarded and the reward is after performing a certain number of transaction。

get a bit。And then you own that bitco and you can spend it so so miners are essentially rewarded for work。

 This is in the bitin world called proof of work So youre essentially work to generate currency and that currency gets added to the entire system So that's the reason miners are even participating Otherwise why would you have machines that are doing all this work for not getting anything out of it So the incentive is you participate in the bitin network after a while you do a certain amount of work you will get a bitin and the amount of bitin that are generated is actually decreasing over time so that the amount of money in the system is actually bounded but that's a separate problem we don't need to worry about that but this ledger can then be essentially used for actually performing transaction So if you have some bitin in your wallet you can go spend it and you are to transfer it and then essentially that transaction saying I spend amount of bitcoins on this transaction will have to go into the ledger。

and get recorded which means that I am transferring my money to someone else wherever I paid it to right so so that's how money is actually being exchanged theres a public record of it and you can always verify that when you are trying to spend it you actually own it before you spend it。

So that's the basic idea it brings together some of the concepts it talked about peer to peer networks。

 consensus， although this is using more sophisticated consensus than that we talked about。

 it uses signatures in terms of public key cryptography。

 so all these elements you put it together to get a cryptocurrency network。Okay， so。

That's all I'm going to say a lot more here than I just gloss to lots of details。

 but you get a very high level idea of how security techniques can be used to boots a cryptocurrency network。

That's all I'll say here it'll wrap up the lecture so I talked about a few different things we talked a little bit about encryption and authentication I talked about key exchange and then we use these ideas to do several different application hashing secure email we ended up with cryptocurrencies so this actually important area of reset distributed security the problem never goes away no matter how many solutions you come back with the bad guys come up with more issues that they can attack your network and so on so there's never a dearth of problems to work on in this area and also things like distributed consensus etc I've gotten a big resurgence presenting fault all and nobody looked at for decades and then once there was money in terms of Bitcoinins has became big area lots of papers now being published people actually making companies out of it and so on but also important from societal perspective that people need secure。

To trust our computing system right So this is why you know design your applications。

 you really have to think about security as well。 Okay， not something we did in the labs and so on。

 but still an important design concept。So if there are no more questions。

 I will end it here one minute early so just。To wrap up we are done with the class for those of you came a little bit late。

 I mentioned that the exam is next Tuesday。At one o'clock same thing as the midterm you can bring one sheet of paper handwritten as a cheat sheet and I also mentioned several times that you only have to worry about lectures 13 through 25 no only need to worry about the material that was already on the midterm that we already covered so best of luck or the exam and have a good summer stop here。



![](img/e742897255c5827254e726d8a9432359_2.png)