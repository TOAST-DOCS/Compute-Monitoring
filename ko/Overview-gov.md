## Compute > Monitoring > 개요

Infrastructure 서비스에서는 사용자가 생성한 인스턴스에 대한 모니터링 기능을 기본으로 제공합니다.
인스턴스의 하드웨어 리소스 사용량을 볼 수 있으며, 사용량에 임곗값을 설정하여 특정 상황에 대한 알람을 이메일 또는 SMS로 받아볼 수 있습니다.

다음은 TOAST 모니터링 시스템 구성은 다음 그림과 같습니다

![[모니터링 시스템 구성]](http://static.toastoven.net/prod_infrastructure/monitoring/gov_img_1.jpg)

모니터링 시스템은 OpenStack의 Ceilometer를 기반으로 확장한 시스템입니다.
기본적으로 하이퍼바이저(hypervisor)를 통해 사용자가 생성한 인스턴스의 리소스 사용량 정보를 얻기 때문에 모니터링을 위한 별도의 프로그램을 설치할 필요가 없습니다.
