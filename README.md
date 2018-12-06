# gsms
golang  aliyun, alidayu sms sdk

Aliyun, Alidayu Sms Api
==========================

--------------------------
Aliyun Sms Example:
--------------------------
    import (
        "github.com/jonsen/gsms"
        "fmt"
    )

    var smsProvider *gsms.SmsProvider

    func init(){
        accessKeyId := "you aliyun accesskey id"
        accessKeySecret := "you aliyun accesskey secret"
        regionId := "cn-hangzhou"
        signName := "you sms sign name"
        smsProvider = gsms.NewAliyunSms(accessKeyId, accessKeySecret, regionId,     signName)
    }

    func AliyunSmsSend(mobiles string) (*gsms.SmsResult, error){
        smsProvider.SetTemplateCode = "sms_123456"
	    params := map[string]string{
		    "code":   "S-123",
		    "time":   "2018-12-04 21:24:33",
	    }
        smsProvider.SetTemplateParam(params)
        return smsProvider.Send(mobiles)
    }

    func main() {
    	result, err := AliyunSmsSend("mobile number")
    	if err != nil {
    		fmt.Println(err)
    	} else {
    		fmt.Printf("%#v", result)
    	}
    }

--------------------------
Alidayun Sms Example:
--------------------------

    import (
        "github.com/jonsen/gsms"
    )

    var smsProvider *gsms.SmsProvider

    func init(){
        appKey := "you alidayu app key"
        appSecret := "you alidayu app secret"
        signName := "you sms sign name"
        smsProvider = gsms.NewAlidayunSms(appKey, appSecret, signName)
    }

    func AlidayuSmsSend(mobiles string) (*gsms.SmsResult, error){
        smsProvider.SetTemplateCode = "sms_123456"
	    params := map[string]string{
		    "code":   "S-123",
		    "time":   "2018-12-04 21:24:33",
	    }
        smsProvider.SetTemplateParam(params)
        return smsProvider.Send(mobiles)
    }

    func main() {
    	result, err := AliyunSmsSend("mobile number")
    	if err != nil {
    		fmt.Println(err)
    	} else {
    		fmt.Printf("%#v", result)
    	}
    }
