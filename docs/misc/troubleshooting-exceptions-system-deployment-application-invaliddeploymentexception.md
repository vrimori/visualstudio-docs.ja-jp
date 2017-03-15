---
title: "例外のトラブルシューティング : System.Deployment.Application.InvalidDeploymentException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidDeploymentException クラス"
ms.assetid: 4361e053-8eaf-44e3-b8ac-95516d8d1832
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Deployment.Application.InvalidDeploymentException
アプリケーションまたはそのアプリケーション マニフェストと配置マニフェストが無効な場合、<xref:System.Deployment.Application.InvalidDeploymentException> 例外がスローされます。  
  
## 関連するヒント  
 **このアプリケーションのマニフェストが有効であることを確認します。**  
 アプリケーション マニフェストは、アプリケーションが実行時にバインドする必要がある共有 side\-by\-side アセンブリとプライベート side\-by\-side アセンブリを記述および指定する XML ファイルです。 このファイルは、アプリケーションのテストで使用したアセンブリ バージョンに一致する必要があります。 アプリケーション マニフェストには、アプリケーションにとってプライベートなファイルのメタデータを記述することもできます。  
  
 **ClickOnce 機能を使用してアプリケーションを配置します。**  
 ClickOnce を使用して、Windows アプリケーションを Web サーバーまたはネットワーク ファイル共有に発行することでインストールを簡略化できます 詳細については、「[ClickOnce のセキュリティと配置](../deployment/clickonce-security-and-deployment.md)」を参照してください。  
  
## 参照  
 <xref:System.Deployment.Application.InvalidDeploymentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)   
 [Windows フォームの ClickOnce 配置](../Topic/ClickOnce%20Deployment%20for%20Windows%20Forms.md)