---
title: "方法 : アクセス許可が制限されたドキュメントでの分離コードの実行を許可する | Microsoft Docs"
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
  - "コード [Visual Studio での Office 開発], 実行 (制限されたドキュメントで分離コードを)"
  - "ドキュメント [Visual Studio での Office 開発], 制限されたアクセス許可"
  - "Information Rights Management [Visual Studio での Office 開発]"
  - "IRM [Visual Studio での Office 開発]"
  - "Office ドキュメント [Visual Studio での Office 開発, 制限されたアクセス許可"
  - "アクセス許可 [Visual Studio での Office 開発]"
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 方法 : アクセス許可が制限されたドキュメントでの分離コードの実行を許可する
  Microsoft Office の Information Rights Management \(IRM\) 機能を使用して、文書やブックに対するアクセス許可を制限できます。  既定では、制限された Microsoft Office Word 文書や Microsoft Office Excel ブックの分離コードは実行できません。  この既定値を変更すると、マネージ コード拡張機能がオブジェクト モデルにアクセスできるようになり、ソリューションが動作します。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 アクセス許可設定を変更するには、ドキュメントまたはブックの作成者であるか、フル コントロール アクセスを保持している必要があります。  
  
### アクセス許可が制限されたドキュメントでの分離コードの実行を許可するには  
  
1.  Word または Excel で文書またはブックを開きます。  
  
2.  **\[ファイル\]** のタブをクリックし、**\[配布準備\]**をポイントし、**\[アクセスの制限\]**をポイントし、**\[アクセス制限あり\]**をクリックします。  
  
    > [!NOTE]  
    >  初めて使用する場合は、Windows Rights Management クライアントをインストールするようにメッセージが表示されます。  クライアントをインストールした後で、手順を繰り返すことが必要になる場合があります。  
  
3.  **\[アクセス権\]**  ダイアログ ボックスで、**\[このドキュメントへのアクセスを制限する\]** を選択し、**\[その他のオプション\]** をクリックします。  
  
4.  **\[ユーザーの追加権限\]** で、**\[プログラムを使ってコンテンツにアクセスする\]** を選択します。  
  
 Word または Excel が、プログラムを利用してオブジェクト モデルにアクセスできるようになります。  
  
## 参照  
 [Information Rights Management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [ドキュメント レベルのソリューションにおけるドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  