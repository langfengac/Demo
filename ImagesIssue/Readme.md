# docker 或linux 中使用 图片类

>一. 引用ZKWeb.System.Drawing
`Install-Package ZKWeb.System.Drawing`

>二. 页面上引用using System.DrawingCore
将原来的
using System.Drawing;
using System.Drawing.Imaging;
改为ZKWeb的 
using System.DrawingCore;
using System.DrawingCore.Imaging;

>三. 修改DockerFile

3.1 加入安装命令
`RUN apt-get update -y && apt-get install -y libgdiplus && apt-get clean && ln -s /usr/lib/libgdiplus.so /usr/lib/gdiplus.dll`
3.2 或直接用 stulzq/dotnet:2.2.0-aspnetcore-runtime-with-image 做为底包

将 FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
改为
FROM stulzq/dotnet:2.2.0-aspnetcore-runtime-with-image AS base
