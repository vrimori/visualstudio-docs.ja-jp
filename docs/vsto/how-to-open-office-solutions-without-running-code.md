---
title: "方法 : コードを実行せずに Office ソリューションを開く | Microsoft Docs"
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
  - "アセンブリ [Visual Studio での Office 開発], バイパス"
  - "バイパス (アセンブリを)"
  - "ドキュメント [Visual Studio での Office 開発], 開く (コードを実行しないで)"
  - "Office ドキュメント [Visual Studio での Office 開発, 開く (コードを実行しないで)"
  - "Office ソリューション [Visual Studio での Office 開発], 開く"
  - "開く (Office ソリューションを)"
  - "ソリューション [Visual Studio での Office 開発], 開く"
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 方法 : コードを実行せずに Office ソリューションを開く
  マネージ コード拡張機能を使用して作成した Microsoft Office ソリューションは、エンド ユーザーの Office アプリケーションのセキュリティ設定が \[高\] に設定されている場合でも実行されます。  これは、.NET アセンブリ コードのセキュリティが、Microsoft Office ではなく、Microsoft .NET Framework によって管理されるためです。  
  
 ただし、コードを実行せずに文書を開くことが必要な場合もあります。  たとえば、文書が開くときに実行されるコードによって内容が変更される可能性があるので、その前に文書の外観を更新しておく場合です。  また、特定の情報を含む文書をだれかに送信するときに、内容が変更される可能性のあるコードを実行したくない場合も考えられます。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 マネージ コード拡張機能が組み込まれた文書やブックを、アセンブリ コードを実行せずに開く方法がいくつかあります。  
  
### Shift キーを使ってアセンブリをバイパスするには  
  
-   Word または Excel で文書が開くときに初期イベントが発生しないように、Shift キーを押しながら、**\[ファイル\]** メニューから文書またはブックを開きます。  
  
    > [!NOTE]  
    >  **作業の開始**タスク ペインから文書またはブックを開く場合は、Shift キーを押しながら実行してもコードはバイパスされません。  文書を開いた後のイベントの発生も回避できません。  
  
     この方法は、先にコードの実行や文書の変更を行わずに、文書を開いて変更を加える場合に適しています。  
  
### アセンブリの名前変更または削除によってアセンブリをバイパスするには  
  
-   アセンブリが配置されているコンピューターで必要なアクセス許可を保持している場合は、文書やブックがアセンブリを検出できないよう、アセンブリ名を変更したり、アセンブリを削除したりできます。  その結果、Office ドキュメントを開くたびにエラーが発生します。  
  
     複数のユーザーによって使用されるソリューションの場合、この方法を使用すると、すべてのユーザーがソリューションを実行できなくなります。  この方法は、コードまたは参照サーバーに問題が見つかったときに、すべてのユーザーがソリューションを実行できないようにする場合に適しています。  
  
## 参照  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office ソリューションにおけるアプリケーション マニフェストと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  