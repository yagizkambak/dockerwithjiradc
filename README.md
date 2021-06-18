# Docker ile JIRA DC Mimarisi

Selamlar herkese,

Bu repository örnek amaçlı oluşturulmuştur. Detaylı bilgi almak için mail atabilirsiniz.

---

### Repository İçeriği

* jira-compose-node1.yml
* jira-compose-node2.yml

## Enviroments

### Docker Compose Environments

| Docker Compose Variable | Açıklama |
| - | - |
| **image** | **Atlassian**'a ait official **Docker** imajını tanımladık. |
| **conatiner_name** | **Docker-Compose** ile ayağa kaldıracağımız **JIRA** konteynerinin adını tanımlıyoruz. |
| **network_mode** | Oluşacak konteynere ait network modu. Biz bu örnekte konteynerımızı makinenin kendisiymiş gibi tanıtmak istediğimiz için host modunu tercih ediyoruz. |
| **volumes** | **JIRA** konteyner içerisindeki ortak alan klasörünün, fiziksel makine üzerinde bind edileceği klasörü tanımlıyoruz. |
| **environment** | **JIRA**’ya ait spesifik konfigürasyonumuzu yapacağımız tanımlamalar olacaktır. |

### JIRA Environments

| JIRA Variable | Açıklama |
| - | - |
| **CLUSTERED** | Bu tanım **JIRA’**nın bize **Cluster** olarak çalışıp çalışmayacağını belirlememizi sağlamakta. Data Center yapısı için bu tanımı **true **olarak set ediyoruz. |
| **JIRA_SHARED_HOME** | Burada **JIRA**’nın diğer nodelar ile paylaşacağı dosyaların dizini belirtmemiz gerekiyor. Bu kısım önemli çünkü **Shared-File System** kısmına bağlanacak yer burası. |
| **JIRA_NODE_ID** | **JIRA**’ya ait node üzerine tanımlanan spesifik id tanımı. Bu tanımı boş bırakırsanız **JIRA**’ya ait konteyner her oluşturulduğunda farklı bir unique id’ye sahip olacaktır. |
| **EHCACHE_LISTENER_HOSTNAME** | Cache iletişimi için **JIRA** konteynerinin çalıştığı makinenin ismi. Bu kısım tanımlanmaz ise **JIRA** bunu otomatik olarak çözümleyecektir. |
| **EHCACHE_LISTENER_PORT** | Cache iletişimi için node’un dinleyeceği port tanımı. Default değer olan **40001** portunu kullanıyoruz. |
| **EHCACHE_OBJECT_PORT** | Aramaların/işlemlerin registry üzerinde remote objelerin bağlı olduğu porta ait tanımı. | 
| **EHCACHE_PEER_DISCOVERY** | Node’ların birbirlerini networkte nasıl bulacağını tanımladığımız kısım. Buradaki değeri bu örnek için **default** olarak bırakabiliriz. |
| **ATL_JDBC_URL** | JIRA'nın kurulu olduğu database adresi. |
| **ATL_JDBC_USER** | Database bağlantısını kurmak için tanımlı kullanıcı |
| **ATL_JDBC_PASSWORD** | Database bağlantısını kurmak için tanımlanmış kullanıcıya ait şifre |
| **ATL_DB_DRIVER** | Kullanılan veritabanına ait driver. Burda örnek olarak postgresql driverını kullandık. |
| **ATL_DB_TYPE** | PostgreSQL kullandığımız için type olarak postgres72 kullanıyoruz. |
| **ATL_DB_SCHEMA_NAME** | public schema üzerine kurulum gerçekleştirmiştik. |
