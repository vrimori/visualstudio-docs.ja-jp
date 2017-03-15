---
title: "方法: ドメイン固有言語の名前空間を変更する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語, namespace"
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 19
---
# 方法: ドメイン固有言語の名前空間を変更する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ドメイン固有言語の名前空間を変更できます。  **\*\*\* DSL Explorer \*\*\***Dsl パッケージのプロジェクトのプロパティアセンブリ情報の変更を行う必要があります。  
  
### ドメイン固有言語の名前空間を変更するには  
  
1.  **\*\*\* DSL Explorer \*\*\***ENT1ENT で\[\] ノードをクリックします。  
  
2.  \[ENT0ENT\] ウィンドウで\[ENT1ENT\] プロパティを変更します。  
  
3.  ソリューションを保存しテンプレートを変換します。  
  
4.  \[ENT1ENT\] メニューの \[ENT2ENT\] をクリックします。  
  
     プロジェクトのプロパティが表示されます。  
  
5.  **\[アプリケーション\]** タブをクリックします。  
  
6.  新しい名前空間名に ENT0ENT \[入力\] プロパティを変更します。  
  
7.  またアセンブリの名前を変更する場合は**\*\*\* Assembly name property. \*\*\*** を変更します。  
  
8.  アセンブリ名を変更した場合は開いている DslPackage \\ Package.tt がこの行を更新し:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. カスタム コードを記述しコード ファイルに名前空間とクラス参照を変更してください。  
  
10. Visual Studio の実験用インスタンスをリセットします。  
  
    1.  **\\Users\\** *{name}* **\\AppData\\Local\\Microsoft\\VisualStudio\\\*Exp** を削除します。  
  
    2.  Windows の \[ENT2ENT\] メニューの \[**\*\*\* All Programs \*\*\*\*\*\* Microsoft Visual Studio 2010 SDK \*\*\* ツール \*\*\* Reset the Experimental Instance \*\*\*** を選択します。  
  
11. \[入力\] ENT0ENT メニューで **ソリューションのリビルド**  を選択します。  
  
## 参照  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/ja-jp/ca5e84cb-a315-465c-be24-76aa3df276aa)