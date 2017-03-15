---
title: "エラー コード | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エラー コードをソース管理プラグイン"
  - "ソース管理プラグインをエラー コード"
  - "エラー [Visual Studio SDK]"
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# エラー コード
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ソース管理プラグインの API 関数がエラーを返したは、次のエラー コードのいずれかを指定すると想定されます。 すべてのエラーが警告または情報エラー コードは正、負の値と、成功した場合は 0 です。  
  
|エラー コード|値|説明|  
|-------------|-------|--------|  
|`SCC_I_SHARESUBPROJOK`|7|2 つの手順でソース管理からファイルを追加するプラグインをサポートします。 詳細については、「[SccSetOption](../extensibility/sccsetoption-function.md)」を参照してください。|  
|`SCC_I_FILEDIFFERS`|6|ローカル ファイルはソース管理データベースにファイルを異なる \(たとえば、 [SccDiff](../extensibility/sccdiff-function.md) この値を返す可能性があります\)。|  
|`SCC_I_RELOADFILE`|5|ローカル ファイルがソース管理の操作中に変更されましたIDE、ファイルの可能な場合は再読み込みする必要があります。|  
|`SCC_I_FILENOTAFFECTED`|4|ファイルが影響を受けません。|  
|`SCC_I_PROJECTCREATED`|3|ソース管理操作中に、プロジェクトの作成 \(への呼び出し中など、 [SccOpenProject](../extensibility/sccopenproject-function.md) と `SCC_OP_CREATEIFNEW` フラグが指定されて\)。|  
|`SCC_I_OPERATIONCANCELED`|2|操作が取り消されました。|  
|`SCC_I_ADV_SUPPORT`|1|指定されたコマンドのオプションを高度なプラグインをサポートします。 詳細については、「[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)」を参照してください。|  
|`SCC_OK`|0|成功。|  
|`SCC_E_INITIALIZEFAILED`|\-1|エラー: 初期化に失敗しました。|  
|`SCC_E_UNKNOWNPROJECT`|\-2|エラー: プロジェクトでは、不明です。|  
|`SCC_E_COULDNOTCREATEPROJECT`|\-3|エラー: プロジェクトを作成できませんでした。|  
|`SCC_E_NOTCHECKEDOUT`|\-4|エラー: ファイル チェック アウトをされていません。|  
|`SCC_E_ALREADYCHECKEDOUT`|\-5|エラー: ファイルは既にチェック アウトをされています。|  
|`SCC_E_FILEISLOCKED`|\-6|エラー: ファイルがロックされています。|  
|`SCC_E_FILEOUTEXCLUSIVE`|\-7|エラー: ファイルが排他的にチェック アウトします。|  
|`SCC_E_ACCESSFAILURE`|\-8|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|`SCC_E_CHECKINCONFLICT`|\-9|エラー: チェックイン中に競合が発生しました。|  
|`SCC_E_FILEALREADYEXISTS`|\-10|エラー: ファイルは既に存在します。|  
|`SCC_E_FILENOTCONTROLLED`|\-11|エラー: ファイルは、ソース管理下ではありません。|  
|`SCC_E_FILEISCHECKEDOUT`|\-12|エラー: ファイルのチェック アウトします。|  
|`SCC_E_NOSPECIFIEDVERSION`|\-13|エラー: 指定されたバージョンはありません。|  
|`SCC_E_OPNOTSUPPORTED`|\-14|エラー: 操作がサポートされていません。|  
|`SCC_E_NONSPECIFICERROR`|\-15|不特定のエラーです。|  
|`SCC_E_OPNOTPERFORMED`|\-16|エラー、操作は実行されませんでした。|  
|`SCC_E_TYPENOTSUPPORTED`|\-17|エラー: バイナリなど、ファイルの種類は、ソース コード管理システムではサポートされていません。|  
|`SCC_E_VERIFYMERGE`|\-18|ファイルは、自動マージにしましたが、保留中のユーザーの確認となっているチェックされていません。|  
|`SCC_E_FIXMERGE`|\-19|ファイルは、自動マージにしましたが、手動で解決しなければなりませんマージの競合によってチェックインされていません。|  
|`SCC_E_SHELLFAILURE`|\-20|シェルの問題が原因のエラーです。|  
|`SCC_E_INVALIDUSER`|\-21|エラー: ユーザーは有効です。|  
|`SCC_E_PROJECTALREADYOPEN`|\-22|エラー: プロジェクトが開いています。|  
|`SCC_E_PROJSYNTAXERR`|\-23|プロジェクトの構文エラーです。|  
|`SCC_E_INVALIDFILEPATH`|\-24|エラー: ファイルのパスは有効です。|  
|`SCC_E_PROJNOTOPEN`|\-25|エラー: プロジェクトは開かれていません。|  
|`SCC_E_NOTAUTHORIZED`|\-26|エラー: ユーザーは、この操作を実行する権限がありません。|  
|`SCC_E_FILESYNTAXERR`|\-27|ファイルの構文エラーです。|  
|`SCC_E_FILENOTEXIST`|\-28|エラー、ローカルのファイルは存在しません。|  
|`SCC_E_CONNECTIONFAILURE`|\-29|エラー: 接続エラーが発生しました。|  
|`SCC_E_UNKNOWNERROR`|\-30|不明なエラーがあります。|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|\-31|バック グラウンドの取得操作が進行中です。|  
  
## クイックをチェックするために用意されているマクロ  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE) IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE) IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## 解説  
 すべてのソース管理プラグインの API 関数 \(を除く、 [SccAdd](../extensibility/sccadd-function.md), 、[SccCheckin](../extensibility/scccheckin-function.md), 、および [SccDiff](../extensibility/sccdiff-function.md)\) 引数として渡されるローカル ファイルが作業フォルダーに存在しない場合に成功すると予測されます。 たとえば、IDE がへの呼び出しを発行ことがあります、 [SccCheckout](../extensibility/scccheckout-function.md) または [SccUncheckout](../extensibility/sccuncheckout-function.md) 作業フォルダーに存在しませんが、ソース管理システムに存在しているファイルにします。 この呼び出しは成功します。 作業フォルダー内、またはソース管理システム内のファイルがない場合にのみが、関数の失敗を想定します。  
  
 などの特定の関数 `SccAdd` と `SccCheckin`, 、具体的に返す必要があります `SCC_E_FILENOTEXIST` 作業フォルダーにファイルが存在しない場合。 作業ファイルが存在しない場合を成功した場合に、関数は、ソース管理システムで有効なファイル名を操作するには、その他の機能が予想されます。  
  
 ソース管理プラグインすることは避けて、ファイルの権限に関する前提条件作業フォルダー内でも、プラグインがマークされている場合、ファイル読み取り専用いくつかの操作中にします。 作業フォルダー内のファイルの移動、削除、および、プラグインのコントロールの外部で変更できます。  
  
## 参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)