---
title: "例外のトラブルシューティング : System.Data.SqlClient.SqlException | Microsoft Docs"
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
  - "SqlException クラス"
ms.assetid: 05f63457-3825-4541-ae09-0c771eb5ba35
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Data.SqlClient.SqlException
SQL Server から警告やエラーが返されると、<xref:System.Data.SqlClient.SqlException> 例外が生成されます。  
  
## 関連するヒント  
 **有効な資格情報で接続しようとしていることを確認します。**  
 指定している資格情報が有効であることを確認します。 詳細については、「[How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)」を参照してください。  
  
 **サーバー名が正しいこと、およびサーバーが動作していることを確認します。**  
 正しいサーバー名を使用していること、およびサーバーに到達できることを確認します。  
  
### コメント  
 この例外は、.NET Framework SQL Server 用データ プロバイダーが、サーバーによって生成されたエラーを検出するたびにスローされます。  
  
 重大度レベルが 10 以下のメッセージは情報メッセージで、ユーザーの入力ミスによってエラーが発生した場合に表示されます。 重大度レベルが 11 ～ 16 のエラーはユーザー側に原因があり、ユーザーによって修正できます。 重大度レベルが 17 ～ 25 のエラーは、ソフトウェアまたはハードウェアのエラーです。 重大度レベルが 17 ～ 19 のエラーが発生したときは、特定のステートメントを実行できない場合がありますが、作業は継続できます。  
  
 重大度レベルが 19 以下の場合、<xref:System.Data.SqlClient.SqlConnection> は開いたままです。 重大度レベルが 20 以上のときは、通常、サーバーは <xref:System.Data.SqlClient.SqlConnection> を閉じます。 ただし、ユーザーは接続を再び開き、続行できます。 どちらの場合も、コマンドを実行しているメソッドによって <xref:System.Data.SqlClient.SqlException> が生成されます。  
  
 SQL Server から送られる警告メッセージと情報メッセージについては、SQL Server Books Online の「トラブルシューティング」セクションを参照してください。  
  
## 参照  
 <xref:System.Data.SqlClient.SqlException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)