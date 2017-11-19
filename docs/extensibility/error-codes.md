---
title: "エラー コード |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 50d05e529a3202f59df53801728b40fee1c68f40
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="error-codes"></a>エラー コード
ソース管理プラグイン API 関数がエラーを返したときに、次のエラー コードのいずれかに必要です。 すべてのエラーが警告または情報エラー コードは正の値に負の場合は、成功した場合は 0 です。  
  
|エラー コード|値|説明|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|2 つの手順でソース管理からファイルを追加するプラグインをサポートします。 詳細については、次を参照してください。 [SccSetOption](../extensibility/sccsetoption-function.md)です。|  
|`SCC_I_FILEDIFFERS`|6|ローカル ファイルとは異なるソース管理データベース内のファイル (たとえば、 [SccDiff](../extensibility/sccdiff-function.md)この値を返す可能性があります)。|  
|`SCC_I_RELOADFILE`|5|ローカル ファイルがソース管理の操作中に変更されましたIDE、ファイルの可能な場合は再読み込みする必要があります。|  
|`SCC_I_FILENOTAFFECTED`|4|ファイルは影響はありません。|  
|`SCC_I_PROJECTCREATED`|3|プロジェクトをソース管理操作中に作成した (たとえば、呼び出し中に[SccOpenProject](../extensibility/sccopenproject-function.md)ときに`SCC_OP_CREATEIFNEW`フラグが指定されて)。|  
|`SCC_I_OPERATIONCANCELED`|2|操作が取り消されました。|  
|`SCC_I_ADV_SUPPORT`|1|プラグインは、指定されたコマンドの詳細オプションをサポートします。 詳細については、次を参照してください。 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)です。|  
|`SCC_OK`|0|成功。|  
|`SCC_E_INITIALIZEFAILED`|-1|エラー: 初期化に失敗しました。|  
|`SCC_E_UNKNOWNPROJECT`|-2|エラー: プロジェクトが正常ではありません。|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|エラー: プロジェクトを作成できませんでした。|  
|`SCC_E_NOTCHECKEDOUT`|-4|エラー: ファイルがチェック アウトされません。|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|エラー: ファイルは既にチェック アウトします。|  
|`SCC_E_FILEISLOCKED`|-6|エラー: ファイルがロックされています。|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|エラー: ファイルが排他的にチェック アウトします。|  
|`SCC_E_ACCESSFAILURE`|-8|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|`SCC_E_CHECKINCONFLICT`|-9|エラー: チェックイン中に競合が発生しました。|  
|`SCC_E_FILEALREADYEXISTS`|-10|エラー: ファイルは既に存在します。|  
|`SCC_E_FILENOTCONTROLLED`|-11|エラー: ファイルは、ソース管理下ではありません。|  
|`SCC_E_FILEISCHECKEDOUT`|-12|エラー: ファイルのチェック アウトします。|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|エラー: 指定されたバージョンはありません。|  
|`SCC_E_OPNOTSUPPORTED`|-14|エラー: 操作がサポートされていません。|  
|`SCC_E_NONSPECIFICERROR`|-15|不特定のエラーです。|  
|`SCC_E_OPNOTPERFORMED`|-16|エラー、処理は実行されませんでした。|  
|`SCC_E_TYPENOTSUPPORTED`|-17|エラー: バイナリ、たとえば、ファイルの種類は、ソース コード管理システムではサポートされていません。|  
|`SCC_E_VERIFYMERGE`|-18|ファイルは、自動マージにしましたが、保留中のユーザーの検証になっているためにチェックされていません。|  
|`SCC_E_FIXMERGE`|-19|ファイルは、自動マージにしましたが、手動で解決しなければならないマージ競合しているのためにチェックインされていません。|  
|`SCC_E_SHELLFAILURE`|-20|シェル エラーによりエラーがあります。|  
|`SCC_E_INVALIDUSER`|-21|エラー: ユーザーは有効です。|  
|`SCC_E_PROJECTALREADYOPEN`|-22|エラー: プロジェクトが開いています。|  
|`SCC_E_PROJSYNTAXERR`|-23|プロジェクトの構文エラーです。|  
|`SCC_E_INVALIDFILEPATH`|-24|エラー: ファイル パスが無効です。|  
|`SCC_E_PROJNOTOPEN`|-25|エラー: プロジェクトは開かれていません。|  
|`SCC_E_NOTAUTHORIZED`|-26|エラー: ユーザーは、この操作を実行する権限がありません。|  
|`SCC_E_FILESYNTAXERR`|-27|ファイルの構文エラーです。|  
|`SCC_E_FILENOTEXIST`|-28|エラー、ローカルのファイルは存在しません。|  
|`SCC_E_CONNECTIONFAILURE`|-29|エラー: 接続エラーが発生しました。|  
|`SCC_E_UNKNOWNERROR`|-30|不明なエラーがあります。|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|バック グラウンドの取得操作が現在進行中です。|  
  
## <a name="macros-provided-for-quick-checking"></a>クイックをチェックするために用意されているマクロ  
  
```cpp  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>コメント  
 すべてのソース管理プラグイン API 関数 (を除く、 [SccAdd](../extensibility/sccadd-function.md)、 [SccCheckin](../extensibility/scccheckin-function.md)、および[SccDiff](../extensibility/sccdiff-function.md)) の引数として渡されるローカル ファイルの場合に成功すると予測されます作業フォルダーに存在します。 たとえば、IDE はへの呼び出しを発行することがあります、 [SccCheckout](../extensibility/scccheckout-function.md)または[SccUncheckout](../extensibility/sccuncheckout-function.md)作業フォルダーに存在しませんが、ソース管理システムに存在するファイル。 この呼び出しは成功します。 作業フォルダー内、またはソース管理システム内のファイルがない場合にのみ、関数は動作しません。  
  
 などの特定の関数`SccAdd`と`SccCheckin`、具体的に返す必要があります`SCC_E_FILENOTEXIST`作業フォルダーにファイルが存在しない場合。 成功、作業ファイルが存在しない場合、関数は、ソース管理システムで有効なファイル名を操作するには、その他の関数が予想されます。  
  
 ソース管理プラグインすることは避けて、ファイルの権限に関する前提条件作業フォルダー内でも、プラグインがマークされている場合、ファイル読み取り専用いくつかの操作中にします。 作業フォルダー内のファイルは、移動、削除、および、プラグインの制御外で変更することができます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)