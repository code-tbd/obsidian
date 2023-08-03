# ffmpeg-go 实现视频流截帧
```go
package test  
  
import (  
    "bytes"  
    "fmt"    ffmpeg "github.com/u2takey/ffmpeg-go"  
    "testing"    "time")  
  
func TestA(t *testing.T) {  
    // ffmpeg -rtsp_transport tcp -i rtsp://admin:hefu888888@192.168.1.66:554 -format image2 -vcodec mjpeg -vframes 1 ./out/0.jpg  
    inputFileName := "rtsp://admin:hefu888888@192.168.1.66:554"  
    in := ffmpeg.Input(inputFileName, ffmpeg.KwArgs{"rtsp_transport": "tcp"})  
  
    for {  
       buf := bytes.NewBuffer(make([]byte, 0, 130*1<<10))  
       outputFileName := generateFileName()  
       outputKwArgs := ffmpeg.KwArgs{  
          "format":  "image2",  
          "vcodec":  "mjpeg",  
          "vframes": 1,  
       }  
       err := in.Output(outputFileName, outputKwArgs).WithOutput(buf).Run()  
       if err != nil {  
          fmt.Println("错误：", err)  
          break  
       }  
  
       fmt.Printf("成功生成文件：%s\n", outputFileName)  
  
       time.Sleep(5 * time.Second)  
    }  
}  
  
func generateFileName() string {  
    return fmt.Sprintf("./out/%s.jpg", time.Now().Format("2006年01月02日15时04分05秒"))  
}
```
