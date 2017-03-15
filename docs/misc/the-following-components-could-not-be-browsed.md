---
title: "The following components could not be browsed: | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_CANNOTBROWSECOM"
  - "VS.Message.0x00006A6D"
  - "VS_E_LOADTYPELIBFAILED"
  - "VS_E_INVALIDCOMCOMPONENT"
  - "VS_E_UNRECOGNIZEDCOMPONENT"
  - "VS.Message.0x00006A6E"
  - "VS.Message.ObjectBrowserErrors"
  - "vs.Message.0x00005AC3"
  - "VS.Message.0x00005AC4"
  - "VS.Message.0x00005AC5"
  - "VS_E_REGFAILEDCOMCOMPONENT"
ms.assetid: 83b03767-eecb-47a4-8029-166308c7dded
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The following components could not be browsed:
このメッセージ ボックスは、\[オブジェクト ブラウザー\] および \[コンポーネントの選択\] ダイアログ ボックスに関連する複数のエラーを一覧表示します。  一般的なエラーには、次のようなものがあります。  
  
## コンポーネントまたはファイルの種類をオブジェクト ブラウザーで表示できません。  
 通常、このエラーが発生するのは、存在しないファイル名や無効なファイル名を指定した場合、あるいはオブジェクト ブラウザーを通じて参照できないファイルを指定した場合です。  
  
#### このエラーを解決するには  
  
-   指定したファイル名が存在し、それが参照できるコンポーネント \(.NET アセンブリ、COM タイプ ライブラリ、またはソース ブラウザー ファイル\) であることを確認します。  
  
## ファイルは、有効な .NET Frameworks または COM コンポーネントではありません。  
 通常、このエラーが発生するのは、指定したコンポーネントが .NET Framework アセンブリまたは COM タイプ ライブラリではない場合です。  
  
#### このエラーを解決するには  
  
-   別のコンポーネントを参照するよう選択します。  
  
## ファイルを COM コンポーネントとして登録することはできません。  
 通常、このエラーが発生するのは、COM コンポーネントのタイプ ライブラリを登録できない場合です。  タイプ ライブラリが存在しないか、破損している可能性があります。  
  
#### このエラーを解決するには  
  
-   コンポーネントを再インストールしてやり直します。  
  
## 登録されたタイプ ライブラリが存在しないか、登録された情報が無効です。  
 指定したタイプ ライブラリが既に存在しないか、有効な情報を含んでいない可能性があります。  
  
#### このエラーを解決するには  
  
-   タイプ ライブラリが存在し、正しく登録されていることを確認します。  
  
## COM タイプ ライブラリの参照に必要なコンポーネントが見つからないか、またコンポーネントが正しく登録されていません。  
 ファイル vstlbinf.dll が見つからないか、正しく登録されていません。  
  
#### このエラーを解決するには  
  
1.  コンピューターで vstlbinf.dll を検索し、regsvr32.exe を使用して登録します。  
  
     または  
  
2.  コンピューターに vstlbinf.dll がない場合は、製品を再インストールします。  
  
## 参照  
 [Object Browser](http://msdn.microsoft.com/ja-jp/f89acfc5-1152-413d-9f56-3dc16e3f0470)   
 [Edit Custom Component Set Dialog Box](http://msdn.microsoft.com/ja-jp/dc995bd7-afbf-4389-ba1c-f377b677ded7)