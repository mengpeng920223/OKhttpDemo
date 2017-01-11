# 1.本demo是基于OKHttp3封装而成，但功能目前尚不完整，现在只提供了正常的GET请求和POST请求，返回的数据直接通过Gson解析成Bean,用法非常方便。
# 2.本demo目前不支持文件上传，后续会再加上。
# 3.使用方法：
必须导包：okhttp3, Gson</br>
权限：网络访问权限</br>

调用方式:[依据链式编程]</br>
    //get请求和post请求方法类似</br>
    OKHttpUtils.newBuilder().url(url).get().build().enqueue(new OKHttpCallBack<UserBean>() {
         /**
          * 获取数据成功，配合Gson解析成javabean
          * 前提是必须要先用gson解析成javabean，然后把javabean的泛型代替T，
          * 例如：OKHttpCallBack<UserBean>,User就是解析出来的，可以直接拿来用
          *
          * @param userBean 解析后得到的数据
          */
          @Override
          public void onSuccess(UserBean userBean) {

          }

         /**
          * 获取数据时链接服务器失败
          *
          * @param code 链接服务器失败的状态码
          */
          @Override
          public void onError(int code) {

          }

         /**
          * 获取数据失败
          *
          * @param call 失败时的call
          * @param e    抛出的异常
          */
          @Override
          public void onFailure(Call call, IOException e) {

          }
    });

主要成员类说明：</br>
OKHttpCallBack.java  网络访问的callback </br>
OKHttpManager.java  处理网络访问</br>
OKHttpUtils.java  OKHttp工具类</br>
RequestParam.java  用于get请求，post请求添加参数</br>
UserBean.java  模板Bean,只需要把下载的数据用gson解析成javabean，然后在返回成功的callback中</br>
               可以直接获取到这个javabean对象，可以用来直接获取各种值。【此方法为同步】</br>
               
## 不足之处欢迎指正，谢谢！本人联系方式：QQ821842708
