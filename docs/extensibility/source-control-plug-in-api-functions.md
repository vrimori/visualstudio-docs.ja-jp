---
title: "ソース管理プラグインの API 関数 | Microsoft Docs"
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
  - "ソース管理プラグインを関数"
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# ソース管理プラグインの API 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ソース コントロールのプラグイン API は、次の関数は、ソース管理プラグインに従ってこの API が実装する必要を提供します。 関数とセマンティクスの署名は、ビット フラグに関連付けられているし、その他のパラメーターは、このリファレンスで詳しく説明します。  
  
## 初期化とハウスキーピング関数  
  
|関数|説明|  
|--------|--------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|プロジェクトを閉じます。|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|指定されたコマンドの詳細設定オプションのユーザーに求めます。|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|プラグインのソース管理のバージョンを返します。|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|ソース管理プラグインを初期化します。 プラグインのインスタンスごとに 1 回呼び出されます。|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|プロジェクトを開きます。|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|さまざまなオプションを設定するために使用するジェネリック関数です。 各オプションが始まる `SCC_OPT_xxx` おり、独自に定義された値のセットです。|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|ときに、ソース管理プラグインは、接続する必要があります。 1 回呼び出されます。|  
  
## 主要なソース管理機能  
  
|関数|説明|  
|--------|--------|  
|[SccAdd](../extensibility/sccadd-function.md)|ソース管理システムに完全修飾パス名で指定されたファイルの配列を追加します。|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|ソース管理システムに既に存在するファイルを参照することができ、それらのファイル部分を現在のプロジェクトを作成します。|  
|[SccCheckin](../extensibility/scccheckin-function.md)|ファイルの配列を確認します。|  
|[SccCheckout](../extensibility/scccheckout-function.md)|ファイルの配列を確認します。|  
|[SccDiff](../extensibility/sccdiff-function.md)|完全修飾パス名とソース管理下にあるバージョンで指定されたローカル ユーザーのファイル間の違いを示しています。|  
|[SccGet](../extensibility/sccget-function.md)|一連のファイルの読み取り専用コピーを取得します。|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|呼び出し元がに関して寄せられるファイルのステータスを確認 \(を介して `SccQueryInfo`\)。|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|ソース管理プラグインにとって意味があるプロジェクトのパスのユーザー入力を求めるプラグインが発生します。|  
|[SccHistory](../extensibility/scchistory-function.md)|ローカル ファイルの完全修飾名の配列の履歴を表示します。|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|現在の状態のファイルの一覧を調べます。 さらに、使用、 `pfnPopulate` ファイルに使用される条件に一致しない場合、呼び出し元に通知するため、 `nCommand`です。|  
|[SccProperties](../extensibility/sccproperties-function.md)|完全修飾ファイルのプロパティを示しています。|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|現在の状態の完全修飾ファイルの一覧を調べます。|  
|[SccRemove](../extensibility/sccremove-function.md)|ソース管理システムから完全修飾ファイルの配列を削除します。|  
|[SccRename](../extensibility/sccrename-function.md)|ソース管理システムで指定されたファイルを新しい名前に変更します。|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|さまざまなソース管理システムの機能にアクセスします。|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|ファイルの配列のチェック アウトを元に戻します。|  
  
## 追加機能 \(ソース コントロールのプラグイン API のバージョン 1.2\) をサポートする関数  
 このグループの関数では、ソース管理プラグインの API のバージョン 1.2 に含まれる追加の機能を定義します。 高度なソース管理機能および機能へのアクセスを提供します。  
  
|関数|説明|  
|--------|--------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|バッチ操作を開始します。|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|既存の親プロジェクトの下で指定された名前をサブプロジェクトを作成します。|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|完全修飾パス名とソース管理データベースの場所で指定されたローカル ユーザーのディレクトリの違いを示しています。|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|現在の状態の完全修飾ディレクトリの一覧を調べます。|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|バッチ操作を終了します。|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|特定のプロジェクト \(プロジェクトが存在する必要があります\) のパスの親を返します。|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|ファイルに複数のチェック アウトを許可するかどうかを確認します。|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|プラグインを作成か MSSCCPRJ を確認します。SCC ファイルです。|  
  
## 高度な機能 \(ソース コントロールのプラグイン API のバージョン 1.3\) をサポートする関数  
 このグループの関数では、ソース管理プラグインの API のバージョン 1.3 に含まれる追加の機能を定義します。 高度なソース管理機能および機能へのアクセスを提供します。  
  
|関数|説明|  
|--------|--------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|ソース管理からファイルの一覧を現在のプロジェクトに追加します。|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|ユーザー インターフェイスがない場合、ソース管理からファイルの一覧を取得します。|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|ローカル ファイルとは異なるソース管理内のファイルの一覧を取得します。|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|ソース管理プラグインでサポートされているような拡張機能を指定するフラグを取得します。|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|ユーザー固有のオプションを取得します。|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|ディレクトリと、プロジェクトまたはソース管理下にあるプロジェクト内のファイルの一覧を調べます。 各ディレクトリとファイル名が検出されましたが、コールバック関数に渡されます。|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|ファイルの一覧に加えられた名前の変更を検証します。 各ファイル名は、その変更の状態を持つコールバック関数に渡されます。|  
  
## 必要条件  
 ヘッダー: scc.h  
  
 \(環境 SDK で提供される一般的なフォルダーに含まれて、既定では *\[ドライブ\]*\\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc; サンプルでは、MSSCCI、VSIP フォルダーに指定されている *\[ドライブ\]*\\Program Files\\VSIP 8.0\\MSSCCI\)。  
  
## 参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [ソース管理プラグインの作成](../extensibility/internals/creating-a-source-control-plug-in.md)