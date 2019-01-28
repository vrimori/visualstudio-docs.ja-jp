---
title: エラー コード |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f05a28ab046c1c0221162bce623a2ccf983f3d43
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958148"
---
# <a name="error-codes"></a>エラー コード
ソース管理プラグイン API 関数がエラーを返したときに次のエラー コードのいずれかを指定することが必要です。 すべてのエラーが警告または情報提供のエラー コードは、正の値は負の値と、成功した場合は 0 です。  
  
|エラー コード|[値]|説明|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|プラグインのサポートが 2 つの手順でソース管理からファイルを追加します。 詳細については、次を参照してください。 [SccSetOption](../extensibility/sccsetoption-function.md)します。|  
|`SCC_I_FILEDIFFERS`|6|ローカル ファイルはソース管理データベース内のファイルから異なる (たとえば、 [SccDiff](../extensibility/sccdiff-function.md)この値を返す可能性があります)。|  
|`SCC_I_RELOADFILE`|5|ローカル ファイルがソース管理の操作中に変更されましたIDE、ファイルの可能な場合は再読み込みする必要があります。|  
|`SCC_I_FILENOTAFFECTED`|4|ファイルが影響を受けません。|  
|`SCC_I_PROJECTCREATED`|3|ソース管理操作中に、プロジェクトの作成 (への呼び出し中など、 [SccOpenProject](../extensibility/sccopenproject-function.md)とき`SCC_OP_CREATEIFNEW`フラグが指定されて)。|  
|`SCC_I_OPERATIONCANCELED`|2|操作が取り消されました。|  
|`SCC_I_ADV_SUPPORT`|1|プラグインは、指定されたコマンドの詳細オプションをサポートします。 詳細については、次を参照してください。 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)します。|  
|`SCC_OK`|0|成功。|  
|`SCC_E_INITIALIZEFAILED`|-1|エラー: 初期化に失敗しました。|  
|`SCC_E_UNKNOWNPROJECT`|-2|エラー: プロジェクトは不明です。|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|エラー: プロジェクトを作成できませんでした。|  
|`SCC_E_NOTCHECKEDOUT`|-4|エラー: ファイル チェック アウトをされていません。|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|エラー: ファイルは既にチェック アウトします。|  
|`SCC_E_FILEISLOCKED`|-6|エラー: ファイルがロックされています。|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|エラー: ファイルが排他的にチェック アウトします。|  
|`SCC_E_ACCESSFAILURE`|-8|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|`SCC_E_CHECKINCONFLICT`|-9|エラー: チェックイン中に競合が発生しました。|  
|`SCC_E_FILEALREADYEXISTS`|-10|エラー: ファイルは既に存在します。|  
|`SCC_E_FILENOTCONTROLLED`|-11|エラー: ファイルは、ソース管理下ではありません。|  
|`SCC_E_FILEISCHECKEDOUT`|-12|エラー: ファイルのチェック アウトします。|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|エラー: 指定されたバージョンはありません。|  
|`SCC_E_OPNOTSUPPORTED`|-14|エラー: 操作がサポートされていません。|  
|`SCC_E_NONSPECIFICERROR`|-15|不特定のエラーです。|  
|`SCC_E_OPNOTPERFORMED`|-16|エラー、操作は実行されませんでした。|  
|`SCC_E_TYPENOTSUPPORTED`|-17|エラー: バイナリなど、ファイルの種類は、ソース コード管理システムではサポートされていません。|  
|`SCC_E_VERIFYMERGE`|-18|ファイルは、自動マージにしましたが、保留中のユーザーの検証となっているチェックされていません。|  
|`SCC_E_FIXMERGE`|-19|ファイルは、自動マージにしましたが、手動で解決する必要のあるマージの競合によりチェックインされていません。|  
|`SCC_E_SHELLFAILURE`|-20|シェルのエラーが原因のエラーです。|  
|`SCC_E_INVALIDUSER`|-21|エラー: ユーザーが無効です。|  
|`SCC_E_PROJECTALREADYOPEN`|-22|エラー: プロジェクトが開いています。|  
|`SCC_E_PROJSYNTAXERR`|-23|プロジェクトの構文エラーです。|  
|`SCC_E_INVALIDFILEPATH`|-24|エラー: ファイル パスが無効です。|  
|`SCC_E_PROJNOTOPEN`|-25|エラー: プロジェクトが開いていません。|  
|`SCC_E_NOTAUTHORIZED`|-26|エラー: ユーザーは、この操作を実行する権限がありません。|  
|`SCC_E_FILESYNTAXERR`|-27|ファイルの構文エラーです。|  
|`SCC_E_FILENOTEXIST`|-28|エラー、ローカル ファイルが存在しません。|  
|`SCC_E_CONNECTIONFAILURE`|-29|エラー: 接続エラーが発生しました。|  
|`SCC_E_UNKNOWNERROR`|-30|不明なエラー。|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|バック グラウンドの取得操作が現在進行中です。|  
  
## <a name="macros-provided-for-quick-checking"></a>クイックをチェックするために用意されているマクロ  
  
```cpp  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Remarks  
 すべてのソース管理プラグイン API 関数 (を除く、 [SccAdd](../extensibility/sccadd-function.md)、 [SccCheckin](../extensibility/scccheckin-function.md)、および[SccDiff](../extensibility/sccdiff-function.md)) の引数として渡されるローカル ファイルの場合は成功する必要があります作業フォルダーにありません。 IDE がへの呼び出しを発行するなど、 [SccCheckout](../extensibility/scccheckout-function.md)または[SccUncheckout](../extensibility/sccuncheckout-function.md)ファイルを作業フォルダーに存在しませんが、ソース管理システムに存在します。 この呼び出しは成功します。 作業フォルダー内、またはソース管理システム内のファイルがない場合にのみが、関数の失敗を想定します。  
  
 などの特定の関数`SccAdd`と`SccCheckin`、具体的に返す必要があります`SCC_E_FILENOTEXIST`作業フォルダーにファイルが存在しない場合。 その他の関数は、成功の作業ファイルが存在しない場合、関数は、ソース管理システムで有効なファイル名を操作する必要があります。  
  
 ソース管理プラグインことは避けてくださいファイルに対する特権に関する前提条件、作業フォルダーでも、プラグインがマークされている場合、ファイル読み取り専用いくつかの操作中にします。 作業フォルダー内のファイルの移動、削除、およびコントロール、プラグインの外部で変更されたことができます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)