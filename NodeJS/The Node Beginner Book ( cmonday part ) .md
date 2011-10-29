# Node����


<a name="about"></a>
## ����
���������ڽ̻��������Node.js������Ӧ�ã������лᴫ������������ġ��߼���JavaScript֪ʶ�����������һ����Hello World���Ľ̡̳�  


<a name="status"></a>
### ״̬
�������Ķ����Ѿ��Ǳ�������հ档��ˣ�ֻ�е����д�������Լ�����°汾Node.js�ĸĶ����ж�Ӧ������ʱ���Ż���и��¡�  

�����еĴ��밸������Node.js 0.4.9�汾�в��Թ���������ȷ������  

<a name="intended-audience"></a>
### ���߶���
�������ʺ����������Ƽ��������Ķ��ߣ� ���ٶ�һ������Ruby��Python��PHP����Java������������������һ���ľ��飻��JavaScript���ڳ�ѧ�׶Σ�������ȫ��һ��Node.js�����֡�  

����ָ���ʺ϶��������������һ������Ŀ����ߣ���˼��˵�����鲻��������������͡����������ƽṹ�ȵ�֮��ķǳ������ĸ��������ܡ�Ҫ�������飬��Щ�����ĸ����Ҷ�Ĭ�����Ѿ����ˡ� 

Ȼ�������黹�ǻ��JavaScript�еĺ����Ͷ�������ϸ���ܣ���Ϊ����������ͬ���������еĺ����Ͷ����кܴ�Ĳ�ͬ��  


<a name="structure"></a>
### ����ṹ  
���걾��֮���㽫���һ��������webӦ�ã���Ӧ�������û����ҳ���Լ��ϴ��ļ���  

��Ȼ�ˣ�Ӧ�ñ���û��ʲô�˲���ģ����Ϊ��ʵ�ָù�����д�Ĵ��뱾�����Ǹ���ע������δ���һ�������������Ӧ�õĲ�ͬģ����иɾ��ذ��롣
�ǲ��Ǻ��������Ժ���������ˡ�  

�����ȴӽ�����Node.js�����н���JavaScript������������������н���JavaScript�����Ĳ��쿪ʼ��  

�����ţ�����������һ���ͳ�ġ�Hello World��Ӧ�ã���Ҳ���������Node.jsӦ�á�  

��󣬻�ʹ������������һ����������������Ӧ�ã�����Ҫ��ɸ�Ӧ����Ҫʵ�ֵĲ�ͬģ�飬����ʼһ��һ�����������ʵ����Щģ�顣  

����ȷ�����ǣ���������У���һ�ѧ��JavaScript��һЩ�߼��ĸ�����ʹ�������Լ�Ϊʲôʹ����Щ����Ϳ���ʵ�ֶ��������������ͬ��ĸ�����޷�ʵ�֡�  

��Ӧ�����е�Դ���붼����ͨ��[����Github����ֿ�](https://github.com/ManuelKiessling/NodeBeginnerBook/tree/master/code/application)����ȡ��  


### Ŀ¼
*  [����](#about)  
    * [״̬](#status)   
    * [���߶���](#intended-audience)   
    * [����ṹ](#structure)  
*  [JavaScript��Node.js](#javascript-and-nodejs)  
    * [JavaScript����](#javascript-and-you)  
    * [�������](#a-word-of-warning)  
    * [��������JavaScript](#server-side-javascript)  
    * [��Hello World��](#hello-world)  
*  [һ�������Ļ���Node.js��webӦ��](#a-full-blown-web-application-with-nodejs)  
    * [����](#the-use-cases)  
    * [Ӧ�ò�ͬģ�����](#the-application-stack)  
*  [����Ӧ�õ�ģ��](#building-the-application-stack)  
    * [һ��������HTTP������](#a-basic-http-server)  
    * [����HTTP������](#analyzing-our-http-server)  
    * [���к�������](#passing-functions-around)  
    * [���������������HTTP������������](#how-function-passing-makes-our-http-server-work)  
    * [�����¼������Ļص�](#event-driven-callbacks)  
    * [����������δ��������](#how-our-server-handles-requests)  
    * [����˵�ģ���������](#finding-a-place-for-our-server-module)  
    * [�������������ġ�·�ɡ�](#whats-needed-to-route-requests)  
    * [��Ϊ����ִ��](#execution-in-the-kindom-of-verbs)  
    * [·�ɸ���������������](#routing-to-real-request-handlers)  
    * [����������������Ӧ](#making-request-handlers-respond)  
        * [��β�������](#how-to-not-do-it)  
        * [�����������](#blocking-and-non-blocking)  
        * [�Է�������������������Ӧ](#responding-request-handlers-with-non-blocking-operations)  
    * [�����õĳ���](#serving-something-useful)  
        * [����POST����](#handling-post-requests)  
        * [�����ļ��ϴ�](#handling-file-uploads)  
* [�ܽ���չ��](#conclusion-and-outlook)  


<a name="building-the-application-stack"></a>
## ����Ӧ�õ�ģ��  

<a name="a-basic-http-server"></a>
### һ��������HTTP������  

<a name="analyzing-our-http-server"></a>
### ����HTTP������  

<a name="passing-functions-around"></a>
### ���к�������  

<a name="how-function-passing-makes-our-http-server-work"></a>
### ���������������HTTP������������  

<a name="event-driven-callbacks"></a>
### �����¼������Ļص�  

<a name="how-our-server-handles-requests"></a>
### ����������δ��������  

<a name="finding-a-place-for-our-server-module"></a>
### ����˵�ģ���������  