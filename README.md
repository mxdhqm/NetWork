# Network
基于AFNetWorking的二次封装

```
/**
 *  HTTP post方式请求
 *
 *  @param url         请求url
 *  @param dict        参数
 *  @param encryptFlag 参数是否加密(未公开，传NULL)
 *  @param success     成功回调
 *  @param failure     失败回调
 *
 *  @return AFHTTPRequestOperation
 */
- (AFHTTPRequestOperation *)post:(NSString *)url
                            reqParms:(NSMutableDictionary *)dict
                         encryptFlag:(BOOL)encryptFlag
                             success:(void (^)(AFHTTPRequestOperation *operation, id responseObject))success
                             failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;

/**
 *  HTTPS post方式请求
 *
 *  @param url         请求url
 *  @param dict        参数
 *  @param encryptFlag 参数是否加密(未公开，传NULL)
 *  @param success     成功回调
 *  @param failure     失败回调
 *
 *  @return AFHTTPRequestOperation
 */
- (AFHTTPRequestOperation *)httpsPost:(NSString *)url
                             reqParms:(NSMutableDictionary *)dict
                          encryptFlag:(BOOL)encryptFlag
                              success:(void (^)(AFHTTPRequestOperation *operation, id responseObject))success
                              failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;

//不弹出提示框
- (AFHTTPRequestOperation *)post:(NSString *)url
                        reqParms:(NSMutableDictionary *)dict
                     encryptFlag:(BOOL)encryptFlag
                         isAlert:(BOOL)isAlert
                         success:(void (^)(AFHTTPRequestOperation *operation, id responseObject))success
                         failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;

//消息setChannel使用
- (AFHTTPRequestOperation *)setChannel:(NSString *)url
                              reqParms:(NSMutableDictionary *)dict
                           encryptFlag:(BOOL)encryptFlag
                               success:(void (^)(AFHTTPRequestOperation *operation, id responseObject))success
                               failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;

// get方式请求服务端
- (AFHTTPRequestOperation *)get:(NSString *)url
                       reqParms:(NSMutableDictionary *)dict
                        success:(void (^)(AFHTTPRequestOperation *operation, id responseObject))success
                        failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;

/**
 * 带进度条的文件下载
 * view:显示进度的View
 * downProgress 下载进度条
 * bytesReadView 显示下载进度百分比 lable
 * totalBytesReadView 显示文件大小、已下载大小 lable
 */
- (void)methodDownload:(NSString *)url
                      showView:(UIView *)view
                 bytesReadView:(UILabel*) bytesReadView
            totalBytesReadView:(UILabel*) totalBytesReadView
                      progress:(UIProgressView *)downProgress
                       success:(void (^)(AFHTTPRequestOperation *operation, id responseObject, NSString* downloadFilePath))success
                       failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;


- (void)methodDownload:(NSString *)url
              downLoadOperation:(AFHTTPRequestOperation *)downLoadOperation
         bytesReadView:(UILabel*) bytesReadView
    totalBytesReadView:(UILabel*) totalBytesReadView
              progress:(UIProgressView *)downProgress
               success:(void (^)(AFHTTPRequestOperation *operation, id responseObject, NSString* downloadFilePath))success
               failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;


/**
 *  下载文件，不管
 */
- (void)methodDownload:(NSString *)url success:(void (^)(AFHTTPRequestOperation *operation, id responseObject, NSString* downloadFilePath))success failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;

/**
 *文件上传,自己定义文件名
 *urlStr:    需要上传的服务器url
 *fileURL:   需要上传的本地文件URL
 *fileName:  文件在服务器上以什么名字保存
 *fileTye:   文件类型  png/file
 *
 */
- (void)postUploadWithUrl:(NSString *)urlStr fileUrl:(NSURL *)fileURL fileName:(NSString *)fileName fileType:(NSString *)fileTye success:(void (^)(id responseObject))success fail:(void (^)())fail;

/**
 *文件上传,文件名由服务器端决定
 *urlStr:    需要上传的服务器url  类似  student/uploadAvatar
 *fileURL:   需要上传的本地文件URL
 *
 */
- (void)postUploadWithUrl:(NSString *)urlStr fileUrl:(NSURL *)fileURL success:(void (^)(id responseObject))success fail:(void (^)())fail;

- (void)postUploadWithUrl:(NSString *)urlStr fileUrl:(NSURL *)fileURL reqParms:(NSMutableDictionary *)dict success:(void (^)(id responseObject))success fail:(void (^)())fail;

/**
 * 获取XML数据 (不会用到token)
 */
- (AFHTTPRequestOperationManager *)XMLDataWithUrl:(NSString *)url
                                         reqParms:(NSMutableDictionary *)dict
                                      encryptFlag:(BOOL)encryptFlag
                                          success:(void (^)(AFHTTPRequestOperation *operation, id responseObject))success
                                          failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;


-(void)uploadURL:(NSString *)url andImageToPost:(UIImage *)imageToPost andParams:(NSMutableDictionary *) params completionHandler:(void (^)(NSURLResponse *response, NSData *data, NSError *error)) handler;

/**
 *  判断是否是网络错误
 *
 *  @param error
 *
 *  @return 
 */
+ (BOOL)isNetWorkError:(NSError *)error;
```