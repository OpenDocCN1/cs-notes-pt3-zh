
# Upper Service Design(Top down)

Requirement

Academic search

Association search

Bole search

Topic browser

User Manager

SearchClassifyService

SearchBoleService

SearchAssociationService

TopicService

UserService

SearchPerson Service

SearchAdvisorService

SearchConfService

SearchPubsService

Index and search Component

Dijkstra Algorithm Component

Topic Model Component

BasicService

# The Architecture of Arnetminer

Academic search

Association search

Bole search

Topic browser

User Manager

Upper Service

SearchClassify Service

SearchAssociationService

SearchBoleService

SearchPerson Service

SearchConf Service

SearchPub Service

UserService

Basic Service

Person Service

Conference Service

Publication Service

UserManager Service

Project Components

PDF Parser Component

Internet Spider Component

Database Connect pool Component

Index and search Component

Topic Model Component

Dijkstra Algorithm Component

Data Sources

Expert's personal homepage

Internet Data

PDF and XML files

# Web服务的实现、部署与测试

王新颖

xinying@jlu.edu.cn

# Outline

- Web service implementation and deploy
  - XFire
  - REST
  - JAX-WS
- vice test
  - Junit
- Web service invoke
  - Ajax

# Xfire – A Java SOAP framework for development and consumption of web services

# Xfire

- Xfire开发Web服务的5个步骤:
  - 接口定义
  - 接口实现
  - 配置
  - 发布
  - 测试

```
package edu.thu.keg.core.webservice;

public interface ArnetminerSearchWebService {
    /**
     * search for person list
     * @param keyword - E.g: Jiawei Han pos:professor aff:Illinois edu:ph.D all:computer
     * @param start_page - the start page number you want to return
     * @param num - the number of persons you want to return for each page
     * @return
     */
    public PersonSearchResult person_search(String keyword, int start_page,int num);
    public PersonSearchResult person_search(String keyword);
    ...
}
```

![](img/431d4828d5c6073b7e23d9eca159cdeb_255_0.png)

```
public class ArnetminerSearchWebServiceImpl implements ArnetminerSearchWebService {
    public PersonSearchResult person_search(String keyword, int start_page,int num){
        if(keyword == null || keyword.length() == 0) {
            return null;
        }
        QueryContactInfoService service = new QueryContactInfoService();
        SearchResult<ContactInformation> results = service.queryContactInfo(keyword, start_page, num);
        return SearchResultConvertor.SearchResultToPersonSearchResult(results);
    }
    public PersonSearchResult person_search(String keyword){
        if(keyword == null || keyword.length() == 0) {
            return null;
        }
        int start_page = 0;
        int num = 10;
        return person_search(keyword, start_page, num);
    }
    ...
}
```

```
<mappings xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://xfire.codehaus.org/schemas/1.0/mapping.xsd">
<mapping>
    <method name="test">
        <parameter index="0" mappedName="userId"/>
        <return-type mappedName="Long" />
    </method>
    <method name="person_search">
        <parameter index="0" mappedName="keyword"/>
        <return-type mappedName="PersonList" componentType="edu.thu.keg.core.model.indexer.PersonSearchResult"/>
    </method>
</mapping>
</mappings>
```

```
<beans xmlns="http://xfire.codehaus.org/config/1.0">
    <service>
        <name>
            ArnetminerSearchWebService
        </name>
        <namespace>
            http://www.arnetminer.org/ArnetminerSearchWebService
        </namespace>
        <serviceClass>
            edu.thu.keg.core.webservice.ArnetminerSearchWebService
        </serviceClass>
        <implementationClass>
            edu.thu.keg.core.webservice.ArnetminerSearchWebServiceImpl
        </implementationClass>
    </service>
</beans>
```

Step4: Release

```
public class ArnetminerSearchWebServiceClient {
    public static void main(String args[]) throws Exception {
        String url = "http://localhost:8080/Arnetminer/services/ArnetminerSearchWebService";
        Service serviceModel = new ObjectServiceFactory().create(ArnetminerSearchWebService.class);
        ArnetminerSearchWebService service = (ArnetminerSearchWebService)new XFireProxyFactory().create(serviceModel, url);
        assert(service != null);
        /* System.out.println(id);*/
        System.out.println("1. test person search...");
        System.out.println("\t querying jie tang...");
        PersonSearchResult results1 = service.person_search("jie tang");
        System.out.println("Got " + results1.getResultCount() + " results!");

        System.out.println("1. test person search...");
        System.out.println("\t querying jie tang...");
        PersonSearchResult results1_1 = service.person_search("jie tang",1,5);
        System.out.println("Got " + results1_1.getResultCount() + " results!");
    }
}
```
