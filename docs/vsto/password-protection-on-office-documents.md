---
title: "Office ドキュメントのパスワード保護 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ドキュメント [Visual Studio での Office 開発], 制限されたアクセス許可"
  - "Office ドキュメント [Visual Studio での Office 開発, 制限されたアクセス許可"
  - "パスワード [Visual Studio での Office 開発], ドキュメント保護"
  - "アクセス許可 [Visual Studio での Office 開発]"
  - "ブック [Visual Studio での Office 開発], 制限されたアクセス許可"
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Office ドキュメントのパスワード保護
  Microsoft Office Word 文書および Microsoft Office Excel ブックにパスワードを設定して、パスワードを知らない人が文書やブックを開くことを防止できます。  **\[パスワード\]** というオプションを使って設定します。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 **\[パスワード\]** が有効になっている既存の文書やブックを使用して、ドキュメント レベルのプロジェクトを作成できます。  Visual Studio での動作は、**\[パスワード\]** が有効になっている Word と Excel のドキュメントで異なります。  
  
 **\[パスワード\]** の詳細については、Word または Excel のヘルプを参照してください。  
  
## Excel と Word の動作  
 Visual Studio で **\[パスワード\]** が有効になっている Excel ブックを開くたびに、Excel はパスワードを要求します。  ソリューションをビルドするときにも、再びパスワードが要求されます。ビルド中に文書が開かれるからです。  
  
 Visual Studio で **\[パスワード\]** が有効になっている Word 文書を最初に開いたときに、Word はパスワードを要求します。  パスワードを正しく入力すると、**\[パスワード\]** が文書から削除され、それ以降は文書を開くときにパスワードの入力が不要になります。  ソリューションの文書を開く前にパスワードを要求する必要がある場合は、最終ビルド後、ソリューションを配置する前に、**\[パスワード\]** を有効にしてください。  
  
## 参照  
 [ドキュメント レベルのソリューションにおけるドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Information Rights Management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [方法 : アクセス許可が制限されたドキュメントでの分離コードの実行を許可する](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  