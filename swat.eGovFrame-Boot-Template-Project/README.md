# 전자정부 표준프레임워크 4.3 eGovFrame Boot Template Project

목차
- [추상 라우팅 데이터 소스](#추상-라우팅-데이터-소스)

## 추상 라우팅 데이터 소스

AbstractRoutingDataSource

https://www.baeldung.com/spring-abstract-routing-data-source

https://spring.io/blog/2007/01/23/dynamic-datasource-routing

```
dependency:go-offline
```

https://maven.apache.org/plugins/maven-dependency-plugin/go-offline-mojo.html

```
swat.eGovFrame-Boot-Template-Project_configuration
clean package

swat.eGovFrame-Boot-Template-Project_configuration (clean package)
clean package

swat.eGovFrame-Boot-Template-Project_configuration (dependency;go-offline)
dependency:go-offline
```

http://localhost:8080/board?bbsId=BBSMSTR_AAAAAAAAAAAA

getURL, getUserName

```java
	/**
	 * 게시판 속성정보 한 건을 상세조회한다.
	 *
	 * @see egovframework.let.cop.bbs.brd.service.EgovBBSAttributeManageService#selectBBSMasterInf(egovframework.let.cop.bbs.brd.service.BoardMasterVO)
	 */
	@Override
	public BoardMasterVO selectBBSMasterInf(BoardMaster searchVO) throws Exception {
		// ---------------------------------
		// 2009.06.26 : 2단계 기능 추가
		// ---------------------------------
		// return attrbMngDAO.selectBBSMasterInf(searchVO);

		DatabaseMetaData databaseMetaData = attrbMngDAO.getSqlSession().getConnection().getMetaData();

		if (log.isDebugEnabled()) {
			log.debug("1. getURL={}", databaseMetaData.getURL());
			log.debug("1. getUserName={}", databaseMetaData.getUserName());
		}

		BoardMasterVO result = attrbMngDAO.selectBBSMasterInf(searchVO);

		if (log.isDebugEnabled()) {
			log.debug("2. getURL={}", databaseMetaData.getURL());
			log.debug("2. getUserName={}", databaseMetaData.getUserName());
		}
```

logging.level.egovframework=DEBUG

```properties
logging.root.level=DEBUG
logging.level.egovframework=DEBUG
```
