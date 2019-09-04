Title: MVN发布本地jar
Date: 2019-06-04
Category: Java
Tags: Java,mvn

mvn deploy:deploy-file -DgroupId=net.xmlerlimin -DartifactId=net.sourceforge.pinyin4j -Dversion=2.5.0 -Dpackaging=jar -Dfile=./lib/pinyin4j-2.5.0.jar -DrepositoryId=账户 -Durl=http://私库服务器/nexus/content/repositories/thirdparty/
