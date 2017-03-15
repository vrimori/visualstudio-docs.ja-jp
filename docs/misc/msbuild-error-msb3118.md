---
title: "MSBuild エラー MSB3118 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.UseApplicationTrustInvalidFrameworkVersion"
helpviewer_keywords: 
  - "MSB3118"
ms.assetid: 9bf5b430-0cfb-4da5-a7f7-04d69f20cce1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3118
**MSB3118: アプリケーションはアプリケーション信頼を使用するように設定されていますが、TargetFrameworkVersion が v3.5 ではありません。**  
  
 このエラーは、<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A> プロパティを `True` に設定し、<xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> プロパティを `v3.5` より低いバージョン \(たとえば `v2.0`\) に設定した場合に発生します。  
  
### このエラーを解決するには  
  
-   <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A> プロパティを `v3.5` 以上に設定します。  
  
## 参照  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.UseApplicationTrust%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 [\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [MSBuild エラー MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild エラー MSB3117](/visual-cpp/misc/msbuild-error-msb3117)   
 [MSBuild エラー MSB3119](../misc/msbuild-error-msb3119.md)   
 [MSBuild エラー MSB3174](/visual-cpp/misc/msbuild-error-msb3174)   
 [MSBuild エラー MSB3185](../misc/msbuild-error-msb3185.md)