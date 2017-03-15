---
title: "MSBuild エラー MSB3116 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.HostInBrowserNotOnlineOnly"
helpviewer_keywords: 
  - "MSB3116"
ms.assetid: bf04c587-d0e2-4d68-bbff-da9a985ea70e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3116
**MSB3116: アプリケーションはブラウザーでホストするように設定されていますが、オンラインとオフラインの使用も設定されています。  アプリケーションをオンラインのみでの使用に変更してください。**  
  
 WPF Web ブラウザー アプリケーションを配置する場合は、<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> プロパティを `True` に設定する必要があります。  <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A> を `True` に設定した場合は、<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> プロパティを `False` に設定する必要があります \(インストールをオンラインでのみ使用できるようにするため\)。  後者の条件が満たされていないと、このエラー メッセージが表示されます。  
  
### このエラーを解決するには  
  
-   <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A> プロパティを `False` に設定します。  
  
## 参照  
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.ApplicationManifest.HostInBrowser%2A>   
 <xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities.DeployManifest.Install%2A>   
 [\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)