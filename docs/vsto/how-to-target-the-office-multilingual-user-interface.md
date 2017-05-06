---
title: "方法 : Office Multilingual User Interface を使用する"
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
  - "グローバリゼーション [Visual Studio での Office 開発], ユーザー インターフェイス ターゲット"
  - "ローカリゼーション [Visual Studio での Office 開発], ユーザー インターフェイス ターゲット"
  - "MUI [Visual Studio での Office 開発]"
  - "Multilingual User Interface [Visual Studio での Office 開発]"
  - "Office アプリケーション [Visual Studio での Office 開発], グローバリゼーション"
  - "Office アプリケーション [Visual Studio での Office 開発], ローカリゼーション"
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 方法 : Office Multilingual User Interface を使用する
  Multilingual User Interface \(MUI\) は Microsoft Office の機能であり、これによりエンド ユーザーは、ユーザー インターフェイス \(UI\) の言語を変更できます。  たとえば、英語の UI で作業しているエンド ユーザーは、UI の言語をスペイン語に変更できます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 アプリケーションを使用する Office ユーザーの言語バージョンが多岐にわたる場合は、ユーザーのコンピューターで動作する Office の言語に合わせて UI 文字列の言語を自動的に変更するコードを追加できます。ただし、ユーザーが正しいリソースをインストールしていることが前提となります。  
  
### Office の現在の UI 設定を調べるには  
  
1.  現在のスレッドの <xref:System.Threading.Thread.CurrentUICulture%2A> プロパティを使用します。  ユーザーのコンピューターで現在動作している Office バージョンの言語に合わせて UI 文字列の言語を設定します。  
  
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreCreatingExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/Sheet1.vb#10)]  
  
## 参照  
 [方法 : プライマリ相互運用機能アセンブリを利用して Office アプリケーションを使用する](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Office ソリューションの遅延バインディング](../vsto/late-binding-in-office-solutions.md)  
  
  