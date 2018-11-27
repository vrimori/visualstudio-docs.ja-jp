---
title: ソース管理プラグイン API 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dcb07c3c49b132cdf12c1a4973af3ebf04dfa74
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796780"
---
# <a name="source-control-plug-in-api-functions"></a>ソース管理プラグインの API 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ソース管理プラグイン API は、次の関数は、ソース管理プラグインに従ってこの API を実装する必要がありますを提供します。 各関数とセマンティクスのシグネチャは、ビット フラグに関連付けられているし、その他のパラメーターはこのリファレンスで詳しく説明します。  
  
## <a name="initialization-and-housekeeping-functions"></a>初期化とハウスキーピング関数  
  
|関数|説明|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|プロジェクトを閉じます。|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|指定したコマンドの詳細設定オプションのユーザーに求めます。|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|プラグイン ソース管理のバージョンを返します。|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|ソース管理プラグインを初期化します。 プラグインのインスタンスごとに 1 回呼び出されます。|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|プロジェクトを開きます。|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|さまざまなオプションを設定するために使用するジェネリック関数。 各オプションが始まる`SCC_OPT_xxx`あり、独自の値の定義済みセット。|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|ときに、ソース管理プラグインは、接続する必要があります。 1 回呼び出されます。|  
  
## <a name="core-source-control-functions"></a>コア ソース制御関数  
  
|関数|説明|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|ソース管理システムへの完全修飾パス名で指定されたファイルの配列を追加します。|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|ソース管理システムに既に存在するファイルの参照をでき、現在のプロジェクトの一環としてそのファイルを行います。|  
|[SccCheckin](../extensibility/scccheckin-function.md)|ファイルの配列を確認します。|  
|[SccCheckout](../extensibility/scccheckout-function.md)|ファイルの配列を確認します。|  
|[SccDiff](../extensibility/sccdiff-function.md)|完全修飾パス名とソース管理下にあるバージョンで指定されたローカル ユーザーのファイル間の相違点を示しています。|  
|[SccGet](../extensibility/sccget-function.md)|一連のファイルの読み取り専用コピーを取得します。|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|呼び出し元がについてよく寄せられるファイルの状態を確認します (を使用して`SccQueryInfo`)。|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|ソース管理プラグインにとって意味のあるプロジェクトのパスをユーザーに確認するプラグインをによりします。|  
|[SccHistory](../extensibility/scchistory-function.md)|ローカル ファイルの完全修飾名の配列の履歴を表示します。|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|現在の状態のファイルの一覧を検証します。 また、使用して、`pfnPopulate`ファイルでの条件が一致しない場合に、呼び出し元に通知するため、`nCommand`します。|  
|[SccProperties](../extensibility/sccproperties-function.md)|完全修飾ファイルのプロパティを示します。|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|現在の状態の完全修飾ファイルの一覧を検証します。|  
|[SccRemove](../extensibility/sccremove-function.md)|ソース管理システムからの完全修飾ファイルの配列を削除します。|  
|[SccRename](../extensibility/sccrename-function.md)|ソース管理システムで、新しい名前に、指定されたファイルの名前を変更します|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|さまざまなソース管理システムの機能にアクセスします。|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|ファイルの配列のチェック アウトを元に戻します。|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>追加機能 (ソース管理プラグイン API のバージョン 1.2) をサポートする関数  
 このグループの関数は、ソース管理プラグイン API のバージョン 1.2 に含まれる追加機能を定義します。 高度なソース管理機能および機能へのアクセスを提供します。  
  
|関数|説明|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|バッチ操作を開始します。|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|既存の親プロジェクトの下で指定した名前のサブプロジェクトを作成します。|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|完全修飾パス名とソース管理データベースの場所で指定されたローカル ユーザーのディレクトリ間の相違点を示しています。|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|現在の状態の完全修飾ディレクトリの一覧を検証します。|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|バッチ操作を終了します。|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|(プロジェクトが存在する必要があります)、指定されたプロジェクトのパスの親を返します。|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|ファイルに複数のチェック アウトを許可するかどうかを確認します。|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|プラグインを作成か MSSCCPRJ を確認します。SCC ファイル。|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>高度な機能 (ソース管理プラグイン API のバージョン 1.3) をサポートする関数  
 このグループの関数は、ソース管理プラグイン API のバージョン 1.3 に含まれる追加機能を定義します。 高度なソース管理機能および機能へのアクセスを提供します。  
  
|関数|説明|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|現在のプロジェクトには、ソース管理からファイルの一覧を追加します。|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|ユーザー インターフェイスのないソース管理からファイルの一覧を取得します。|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|ローカル ファイルとは異なるソース管理内のファイルの一覧を取得します。|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|ソース管理プラグインでサポートされている拡張機能を指定するフラグを取得します。|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|ユーザー固有のオプションを取得します。|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|ディレクトリおよびファイルをプロジェクトまたはソース管理下にあるプロジェクトの一覧を検証します。 各ディレクトリとファイル名が見つかりましたが、コールバック関数に渡されます。|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|ファイルの一覧に加えられた名前の変更について説明します。 各ファイル名は、その状態の変更のコールバック関数に渡されます。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: scc.h  
  
 (環境の SDK で提供される一般的なにはフォルダーが含まれます、既定で *[ドライブ]* \Program Files\VSIP 8.0\EnvSDK\common\inc; サンプルでは、MSSCCI、VSIP フォルダーの中でも提供 *[ドライブ]* \ProgramFiles\VSIP 8.0\MSSCCI)。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [ソース管理プラグインの作成](../extensibility/internals/creating-a-source-control-plug-in.md)

