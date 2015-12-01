Microservices: It��s not (only) the size that matters, it��s (also) how you use them �C part 1

> https://www.tigerteam.dk/2014/micro-services-its-not-only-the-size-that-matters-its-also-how-you-use-them-part-1/

�� "SOA �C Hierarchy or organic growth?" �����ἰ�ļ������ĵĿ����׶����ڵ��ˡ��� "SOA : synchronous communication, data ownership and coupling" һ���������ᵽ���ĸ��������ܹ���ԭ���ر��ע�˷����˫��ͨ��ʱ�ķ���߽���������⡣������Щ�����������ǿ�ʼ���ĵ����⡣

�����±������ԣ��������۵��� Microservices��΢���񣩣�΢����ܹ��Ƕ�Ӧ Monolithic�������򣩼ܹ�����һ�ּܹ����������� SOA �������ȱ����ȷ����һ����΢����Ҳû��һ����ȷ�Ķ��塣Ŀǰ����ܴ�ɵĹ�ʶ��΢����Ӧ����С�ģ����ҷ����ǿ��Զ�������ġ��ܶྭ�鷨��˵΢����Ӧ���� 10 �� 100 �д��룬�Ҿ����ô���������Ϊ���з������ȵı�׼�е������ͷ��

����ȱ��һ��׼����ָ�����Ǵ�ҵ��Χ�ͼ��ɷ�ʽ�����΢����û������˼�룬�ڻ��ӵ�ҵ������ƺ��ʵ�΢�������ӹȿ���ɸѡ����һ�����ѣ����Һ������ܵ��ֲ� SOA ��ģʽ����ͼ�����ջ������ߵ����鷨�����·�ϡ�

��ͳ�ķֲ� SOA ��ķ�����΢����ô��

![�ֲ� SOA Ҳ��΢����ܹ���](https://www.tigerteam.dk/wp-content/uploads/2014/01/Layered-SOA.png)

��ͳ�ķֲ������������Entity/Data Services �������� Repository/Data Access Object ��һ��ܱ��ķ���ʵ�������ǹ�ϵ�����ݿ�֮�ϰ���һ�㱡���Ŀǡ�ʹ�ò�ͬ�ı�����ԺͿ�ܣ�Repository һ���� 10 �� 300 �д����װ�� REST �� Web �������ʽ��¶����������΢��������������й���

Task Services ��Э���ͱ��Ŷ�� Entity Service �ĺܱ��ķ���ʹ�ò�ͬ�Ŀ�ܺͿ��Լ�����ת���ĳ̶ȣ�Task Services һ���� 10 �� 1000 �д�����ʵ�֣�����΢��������������й���Ҳֻ�Ƿ��϶��ѡ�

Process Services ������Э����� Task Services �� Entity Services ��һ��ϱ��ķ��񡣵�������»ᴦ��һЩ����ת��������ʧ��ʱ�Ĳ�������ʱ�����е���������⡣ʹ�ò�ͬ�Ŀ�ܺͿ⣬Process Services һ���� 100 �� ��ǧ�д��룬����΢��������������й��򣬺ðɣ��������ϡ�

������ "SOA: synchronous communication, data ownership and coupling" ���ж�˫��ͨ�ŵ����ۣ��ڷֲ� SOA �ܹ��£��������������ͷ������������صĲ�ȷ���ԡ����� Process Service �� Task Service Ҳ�൱�ĸ��ӡ������ͬ�ͷ����ͻ������Ҳ�����⣬ͨ�����緽ʽ���ö��������ӳ�ʱ�䣨���������õ��յ�Ӧ���ʱ�䣩Ҳ�ܳ���

��ǰ������ӣ����Ͱ�����������΢������з���ľ��鷨�����ǿ�����ϵ��϶� Entity/Task/Process Service ����΢�����������ı����˳�ʹ�ô������������ַ����ǲ���΢�������������⡣

������ǽ߾����ܵطֽ����Ϊ�ǳ�С�ķ���ʹ��˫�����ʱ�ӳ�ʱ�佫�ǳ����¡����΢����Ľ�����ڷ���Ĵ�С�϶�����ʹ��ģʽ�ϣ������������ǽ���һ�����������״ͼ��һ��Ӧ�õ���һ�����񣬷�����ŵ���һ��С�ķ�����Щ������ŵ�����һ�ѷ�������ʹ��ģʽ����������ɷ����ѭ�����á�

![΢����ͬ��˫��ͨ����״ͼ��������÷���Ȼ�󱻵��÷����ֵ�����������Ȼ�󡭡�](https://www.tigerteam.dk/wp-content/uploads/2014/02/Microservices_star.png)

���ǳ��Էֽ���񵽷ǳ�С�����ȣ����һ��������Ҫ�ٵ��úܶ�����������Լ�������������Ϊ���Ƕ���Ҫ�Է������ݺ͹��ܡ�

��������һ��Ŀ�������ã���ô��֤�����ܵ����ã�ʹ���еķ��񾡿��ܵ�С�������������ڲ�ͬ�ĳ������Ա����ã��������߼��ǶԵģ��������ǣ�ÿ�������������÷���ʱҲ��������ϡ�����������һ��Ŀ���Ǽ�����ϣ�������ϲ����ڱ�����ҵ�ͼ�����Ҫ���ǰ���º����׵ĶԷ�������޸ġ�

�� "SOA: synchronous communication, data ownership and coupling" һ���У�����������ͬ��˫����õ��µ�һЩ���ӵ�������˾�����
  ͨ����ص���ϣ����ݺͷ���������һ�������ڣ�
  �ֲ���ϣ�ҵ��Ͱ�ȫ���־û��Ȳ���һ�������ڣ�
  ��ʱ��ϣ����������������������޷�����ʱ���񲻿��ã�

����е��¼��������õ����򡣵��޸ķ���Э��ʱ������ʹ�ø÷������������Ҫ�����޸ġ������񲻿���ʱ�����������ڸ÷������������Ҳ�������ˡ���һ�������������ʧ�ܣ����� Process Services ����������Ҳ��ҪӦ�Ը���ʧ�ܵ�Ӱ�졣

![�������ڷ����յ���Ϣִ�и��²���ǰ�����Ļ��Ǹ��²��������ģ�](http://www.tigerteam.dk/wp-content/uploads/2014/02/Service-call-failing.png)

��ͼ�дӿͻ��˷������ĵ��ã����ߴӷ����е�����һ��������Ϊʹ��˫��ͨ�ţ��ͻ��˷���һ��������Ϣ�����񣬷����յ�����ִ��һЩ����������������ݿ⣬������ɺ󣬷�����һ��Ӧ����Ϣ���ͻ��˱��������Ľ����ͨ�ž������磬���� HTTP ���û��� Queue ��Ϣ������������ Monolithic ������ʽ�µ��ڴ淽�����ã����������ǻ����Ҳ��ȶ��ġ�

����ͻ����յ���ʱӦ��������� IO ���󣬵�����������ֿ��ܣ�
  ����û�е�������������ݿ�û�б����¡�
  �����յ��������Ҹ��������ݿ⣬���ǿͻ���û�յ�Ӧ��

ȱ�ٿɿ�����Ϣ������ζ�ſͻ��˲�֪���������˻���û��������ͻ�������һ�����⣬�ͻ���Ҫ��ô���أ�
  �����ʷ����Ƿ������������û�������·�����ã�
  ���ǲ��ʵ�ֱ�ӷ������ԣ�
  ������������
  ���Ƿ������ã�

���ķ�Ӧ��������Ҫ�Ľ��������

����ͻ��˳����ٴε��ã��������ʵ��Ϊ�ܴ�����һ��������Ϣ�Ķ�ε��ã���Ȼ��֤ҵ��ֻ��ִ��һ�Σ�Ҳ����˵����������ݵȵġ�����Ƕ�������һϵ�и��²��������Ǳ������һ���޴��һ����������Ϊ����û��Ҳ��Ӧ���зֲ�ʽ������Э����Щ���¡����������� "SOA: synchronous communication, data ownership and coupling" һ����̸���ģ�˫��ͨ�ŵĲ����߼��Ȳ���΢�������Ҳ���Ǽ򵥵ġ�

![ͬ��˫��ͨ�ŷ�ʽ�������񲹳�](http://www.tigerteam.dk/wp-content/uploads/2014/02/synchronous-SOA-orchestration.png)

����һ������΢����ļܹ���ÿ������ֻ����ʵ���һ�����ԣ��ȴ�ʱ�����һ���޴�����⣬�ȶ��ԡ�Э��������úͲ���Ҳ���Ǿ޴�����⡣����һ����û�ҵ���ȷ�ķ������ָ��׼��

��һƪ�������ǽ�̸����ô�ڷֲ�ʽ�������ɷ��񣬲���һ�·������ȶԼ��ɵ�Ӱ�졣