---
title: "Visual Studio 内での Office 機能の使用 | Microsoft Docs"
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
  - "Office アプリケーション [Visual Studio での Office 開発]"
  - "Office 機能 (Visual Studio 内での)"
  - "セキュリティ [Visual Studio での Office 開発], ドキュメント保護"
ms.assetid: 593fd583-57e5-4ed5-8489-89f73b886c6c
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Visual Studio 内での Office 機能の使用
  ドキュメント レベルのプロジェクトを作成すると、ドキュメントおよび関連アプリケーションは Visual Studio 内でホストされるため、これらのドキュメントを直接デザインし、操作することができます。  Visual Studio で Microsoft Office アプリケーションを開いた場合、そのアプリケーションは基本的には正常に動作します。  ただし、そのアプリケーションの一部の機能が本来とは異なっていたりアクセスできなかったりすることがあります。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## ドキュメントの保護  
 Microsoft Office Word および Microsoft Office Excel には、プロジェクトで使用できるドキュメント保護機能があります。  ただし、Visual Studio でドキュメントを開いているときにドキュメントの保護を有効にすると、デザインを変更できなくなることがあります。  詳細については、「[ドキュメント レベルのソリューションにおけるドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)」を参照してください。  
  
## Information Rights Management  
 Information Rights Management \(IRM\) は Microsoft Office Word および Microsoft Office Excel で使用できます。  IRM によって、承認されていないユーザーによる機密情報の参照や変更を防止することができます。  ただし、IRM が原因でコードを実行できなくなることもあります。  詳細については、「[Information Rights Management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)」を参照してください。  
  
## パスワード保護  
 Microsoft Office Word 文書および Microsoft Office Excel ブックをパスワードがなければ開くことができないように設定できます。  パスワード保護の処理方法は Word と Excel で異なり、開発プロセスに影響を及ぼすことがあります。  詳細については、「[Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)」を参照してください。  
  
## 参照  
 [ドキュメント レベルのソリューションにおけるドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Information Rights Management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [方法 : コードを実行せずに Office ソリューションを開く](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  