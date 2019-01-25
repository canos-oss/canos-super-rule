# canos-super-rule
super rule for canos java projects

## 推送到maven中央仓储步骤
1. 更新本地maven配置
```
  <servers>
    <server>
      <id>ossrh</id>
      <username>{username}</username>
      <password>{password}</password>
    </server>
  </servers>
```

2. 安装到本地仓储(注意，这个安装到本地的包不能直接部署到中行仓储)
```
mvn clean install
```

3. 部署到中央仓储(需要在这个命令里面生产签名)
```
mvn clean deploy -Dgpg.skip=false
```

## 更新 2019-01-25

继承自super-rule的项目，每次`maven clean install`的时候，都要输入gpg密钥，这个比较麻烦。

因此，增加如下配置，默认跳过此插件。
```xml
<configuration>
    <skip>${gpg.skip}</skip>
</configuration>
```

需要push到maven中央仓储的时候，再从命令行使此值为true
