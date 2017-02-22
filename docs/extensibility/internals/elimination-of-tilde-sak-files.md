---
title: "削除する ~ SAK ファイル | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "一時ファイル"
  - "~ sak ファイル"
  - "ソース管理プラグイン ~ SAK ファイル"
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 削除する ~ SAK ファイル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理プラグイン API 1.2 では ~SAK ファイルが検出できるフラグと新しい関数とソース管理プラグインは MSSCCPRJ ファイルと共有チェック アウトをサポートするかどうか置き換えられました。  
  
## ~SAK ファイル  
 Visual Studio .NET 2003 では ~SAK が付けられた一時ファイルを作成します。  これらのファイルがソース管理のプラグインでサポートするかどうかを確認するために使用されています :  
  
-   MSSCCPRJ.SCC ファイル。  
  
-   複数のチェック アウト \(共有\)。  
  
 サポートするプラグインの最新機能はソース管理プラグイン API で 1.2 以降のセクションでは詳細な新機能フラグを使用して一時ファイルを作成せずにこれらの IDE 機能を検出すると関数提供します。  
  
## 新しい機能のフラグ  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## 新しい関数  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 ソース管理プラグイン内で複数のチェック アウト \(共有\)および参照が `SCC_CAP_MULTICHECKOUT` の機能を宣言し`SccIsMultiCheckOutEnabled` の関数を実行します。  この関数はチェック アウト操作がソース・コード管理プロジェクトに発生するたびに呼び出されます。  
  
 ソース管理プラグインを作成および MSSCCPRJ.SCC ファイルを使用するとサポート `SCC_CAP_SCCFILE` の機能を宣言し[SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md) を実行します。  この関数はファイル リストと呼びます。  Visual Studio がそのページ用に MSSCCPRJ.SCC ファイルを使用するかどうかを示す各ファイルの関数の戻り値 `TRUE/FALSE`。  これらの新機能と機能をサポートしていないためソース管理プラグインを選択した場合はこれらのファイルの作成を無効にするには次のレジストリ キーを使用して :  
  
 \[HKEY\_CURRENT\_USER \\ Software \\ Microsoft \\ VisualStudio \\ 8.0 \\ SourceControl 入力\] DoNotCreateTemporaryFilesInSourceControl 「 " \=dword: 00000001  
  
> [!NOTE]
>  このレジストリ キーがダブル ワードに設定されている場合 : 00000000 の場合存在しないキーであるとVisual Studio は一時ファイルを作成しようとします。  ただしレジストリ キーがダブル ワードに設定されている場合 : Visual Studio 00000001 では一時ファイルを作成できません。  代わりにソース管理プラグインが MSSCCPRJ.SCC ファイルをサポートしないため共有チェック アウトをサポートしないと仮定します。  
  
## 参照  
 [ソース管理プラグイン API バージョン 1.2 の新機能します。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)