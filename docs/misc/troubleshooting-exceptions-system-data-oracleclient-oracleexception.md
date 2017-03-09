---
title: "例外のトラブルシューティング : System.Data.OracleClient.OracleException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "OracleException クラス"
  - "Oracle"
  - "例外、Oracle"
ms.assetid: 08b9206e-baa9-4caa-b0c7-ece2118f6e2d
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Data.OracleClient.OracleException
Oracle データベースや .NET Framework Oracle 用データ プロバイダーから警告やエラーが返されると、<xref:System.Data.OracleClient.OracleException> 例外が生成されます。  
  
## 関連するヒント  
 **有効な資格情報で接続しようとしていることを確認します。**  
 指定している資格情報が有効であることを確認します。  
  
 **サーバー名が正しいこと、およびサーバーが動作していることを確認します。**  
 正しいサーバー名を使用していること、およびサーバーに到達できることを確認します。  
  
## 解説  
 この例外は、<xref:System.Data.OracleClient.OracleDataAdapter> が、サーバーによって生成されたエラーを検出したときにスローされます。  
  
 エラーの重大度レベルが高すぎる場合、サーバーは <xref:System.Data.OracleClient.OracleConnection> を閉じることがあります。 ただし、ユーザーは接続を再び開き、続行できます。  
  
## 参照  
 <xref:System.Data.OracleClient.OracleException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)