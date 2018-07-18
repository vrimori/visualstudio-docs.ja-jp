---
title: 機能フラグ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9be7a6a6d1b4ff389859ac2d3ed4aef2c1b0488
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108389"
---
# <a name="capability-flags"></a>機能フラグ
SCC_CAP_*xxx*フラグは、ソース管理プラグインの機能を示すために使用します。 SCC_EXCAP_*xxx*フラグは、拡張機能を示すし、解決するには整数値を増分フラグ。  
  
|機能コード|[値]|説明|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|では、 [SccRemove](../extensibility/sccremove-function.md)とコマンド。|  
|`SCC_CAP_RENAME`|0x00000002L|では、 [SccRename](../extensibility/sccrename-function.md)とコマンド。|  
|`SCC_CAP_DIFF`|0x00000004L|では、 [SccDiff](../extensibility/sccdiff-function.md)とコマンド。|  
|`SCC_CAP_HISTORY`|0x00000008L|では、 [SccHistory](../extensibility/scchistory-function.md)とコマンド。|  
|`SCC_CAP_PROPERTIES`|0x00000010L|では、 [SccProperties](../extensibility/sccproperties-function.md)とコマンド。|  
|`SCC_CAP_RUNSCC`|0x00000020L|では、 [SccRunScc](../extensibility/sccrunscc-function.md)とコマンド。|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|では、 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)とコマンド。|  
|`SCC_CAP_QUERYINFO`|0x00000080L|では、 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)とコマンド。|  
|`SCC_CAP_GETEVENTS`|0x00000100L|では、 [SccGetEvents](../extensibility/sccgetevents-function.md)とコマンド。|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|では、 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)とコマンド。|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|では、 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)とコマンド。|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|チェック アウト時のコメントをサポートしています。|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|チェックイン時にコメントをサポートしています。|  
|`SCC_CAP_COMMENTADD`|0x00002000L|追加コメントをサポートしています。|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|削除時にコメントをサポートしています。|  
|`SCC_CAP_TEXTOUT`|0x00008000L|IDE に用意されている出力関数にテキストを書き込みます。|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|デルタせずにファイルを格納するをサポートします。|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|複数のファイル履歴をサポートしています。|  
|`SCC_CAP_IGNORECASE`|0x00800000L|大文字と小文字のファイルの比較をサポートしています。|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|ファイルの空白文字を区別しない比較をサポートします。|  
|`SCC_CAP_POPULATELIST`|0x02000000L|余分なファイルの検索をサポートします。|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|サポートのコメントは、プロジェクトを作成します。|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|すべての状態の管理下にある場合の相違をサポートします。|  
|`SCC_CAP_GET_NOUI`|0x20000000L|プラグインがサポートしていません UI、Get の IDE を呼び出すことがまだ[SccGet](../extensibility/sccget-function.md)です。|  
|`SCC_CAP_REENTRANT`|0x40000000L|プラグインは、再入可能でスレッド セーフです。 バージョン 1.0 でプラグインがないと仮定します再入可能でスレッド セーフであります。 プラグイン 1.1 では、このビットを設定、ホストが許可された場合を並列で複数のプロジェクトを開きます。|  
  
## <a name="capability-bits-added-in-version-12"></a>バージョン 1.2 で追加された機能ビット  
  
|機能コード|[値]|説明|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|では、 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)です。|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|では、 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)です。|  
|`SCC_CAP_BATCH`|0x00040000L|では、 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)と[SccEndBatch](../extensibility/sccendbatch-function.md)です。|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|では、 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)です。|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|では、 [SccDirDiff](../extensibility/sccdirdiff-function.md)です。|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|ファイルに複数のチェック アウトをサポートしていると、 [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)です。|  
|`SCC_CAP_SCCFILE`|0x80000000L|MSSCCPRJ をサポートしています。SCC ファイル (対象ユーザーと管理者の上書き) および[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)です。|  
  
## <a name="capability-bits-added-in-version-13"></a>バージョン 1.3 で追加された機能ビット  
 これらのフラグが渡されるを一度に 1 つずつ、 [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)機能がサポートされているかどうかを判断する関数。  
  
|拡張機能コード|[値]|説明|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|では、`SCC_CHECKOUT_LOCALVER`チェック アウトのためのオプションです。|  
|`SCC_EXCAP_BACKGROUND_GET`|2|では、 [SccBackgroundGet](../extensibility/sccbackgroundget-function.md)です。|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|では、 [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)です。|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|余分なディレクトリの検索をサポートします。|  
|`SCC_EXCAP_QUERYCHANGES`|5|ファイルの変更の列挙をサポートします。|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|では、 [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)です。|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|では、 [SccGetUserOption](../extensibility/sccgetuseroption-function.md)です。|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|複数のスレッドを SccQueryInfo を呼び出すことができます。|  
|`SCC_EXCAP_REMOVE_DIR`|9|SccRemoveDir 関数をサポートしています。|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|チェック アウトしたファイルを削除できます。|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|チェック アウトしたファイルの名前を変更できます。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)