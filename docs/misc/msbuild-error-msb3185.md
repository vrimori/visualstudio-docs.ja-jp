---
title: "MSBuild エラー MSB3185 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.NoEntryPoint"
helpviewer_keywords: 
  - "MSB3185"
ms.assetid: 032c63c5-d662-42ba-84e1-e3ccca8cee05
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3185
**MSB3185: EntryPoint がマニフェストに指定されていません。**  
  
 このエラーは、マニフェストにエントリ ポイントが指定されていない場合に生成されます。  このエラーは、アプリケーション マニフェストと配置マニフェストの両方に適用されます。  
  
### このエラーを解決するには  
  
-   GenerateApplicationManifest タスクを使用する場合は、有効なエントリ ポイントを指定するか、TargetFrameworkVersion プロパティを "v3.5" 以上に設定してください。  アプリケーション マニフェストの場合、有効なエントリ ポイントは .exe ファイルです。  
  
-   GenerateDeploymentManifest タスクを使用する場合は、有効なエントリ ポイントをマニフェストに指定してください。  配置マニフェストの場合、有効なエントリ ポイントはアプリケーション マニフェストです。  
  
## 参照  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest.TargetFrameworkVersion%2A>   
 [\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [\<PackageFiles\> 要素](../deployment/packagefiles-element-bootstrapper.md)   
 [MSBuild エラー MSB3116](../misc/msbuild-error-msb3116.md)   
 [MSBuild エラー MSB3117](/visual-cpp/misc/msbuild-error-msb3117)   
 [MSBuild エラー MSB3118](../misc/msbuild-error-msb3118.md)   
 [MSBuild エラー MSB3174](/visual-cpp/misc/msbuild-error-msb3174)