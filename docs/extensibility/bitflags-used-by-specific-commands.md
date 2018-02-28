---
title: "特定のコマンドで使用されるビットフラグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: be102b5eaf39db2fc7495c62c456e35e54ffd0f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="bitflags-used-by-specific-commands"></a>特定のコマンドで使用されるビットフラグ
1 つの値の 1 つ以上のビットを設定して、さまざまなソース管理プラグイン API の関数の動作を変更できます。 これらの値は、ビットフラグと呼ばれます。 ソース管理プラグイン API によって使用されるさまざまなビットフラグの詳細をここでは、それらを使用する関数によってグループ化します。  
  
## <a name="checked-out-flag"></a>チェック アウト フラグ  
 いずれかのこのフラグを設定することができます、 [SccAdd](../extensibility/sccadd-function.md)または[SccCheckin](../extensibility/scccheckin-function.md)です。  
  
|フラグ|値|説明|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|ファイルをチェック アウトしてください。|  
  
## <a name="add-flags"></a>フラグを追加します。  
 これらのフラグを使用して、 [SccAdd](../extensibility/sccadd-function.md)です。  
  
|フラグ|値|説明|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|ソース管理プラグインは、ファイルがテキストかバイナリかどうかを自動的に検出すると想定されます。|  
|`SCC_FILETYPE_TEXT`|0x01|ファイルの種類は、テキストです。|  
|`SCC_FILETYPE_BINARY`|0x04|ファイルの種類はバイナリです。 **注:** `SCC_FILETYPE_TEXT`と`SCC_FILETYPE_BINARY`フラグは相互に排他的です。 1 つずつ、またはどちらも設定します。|  
|`SCC_ADD_STORELATEST`|0x02|最新のバージョンのみ (デルタなし) を格納します。|  
  
## <a name="diff-flags"></a>Diff フラグ  
 [SccDiff](../extensibility/sccdiff-function.md) diff 操作のスコープを定義するため、これらのフラグを使用します。 `SCC_DIFF_QD_xxx`フラグは相互に排他的です。 いずれかのファイルが指定されている場合、視覚的なフィードバックはありませんを付与します。 「クイック差分」(QD) プラグインによって決定されないファイルが異なる場合にのみ、異なる方法です。 これらのフラグを指定したにない場合、「visual 比較」が行われます。詳細なファイルの相違点が計算され、表示されます。 要求された QD はサポートされていない場合、プラグインが最適なものを次に移動します。 インスタンスの場合、IDE は、チェックサムを要求し、プラグインが対応していない、プラグインは全内容を確認 (まだよりも早く視覚的に表示)。  
  
|フラグ|値|説明|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|小文字の相違を無視します。|  
|`SCC_DIFF_IGNORESPACE`|0x0004|空白の相違を無視します。 **注:** 、`SCC_DIFF_IGNORECASE`と`SCC_DIFF_IGNORESPACE`フラグは省略可能なビットフラグします。|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|ファイルの内容全体を比較することによって QD です。|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|チェックサムで QD です。|  
|`SCC_DIFF_QD_TIME`|0x0040|ファイルの日付/時刻スタンプによって QD です。|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|これは、すべての QD ビットフラグを確認するために使用されたマスクです。 関数に渡すことはできません次の 3 つの QD ビットフラグは相互に排他的です。 QD には、UI の表示を常に意味するものはありません。|  
  
## <a name="populatelist-flag"></a>PopulateList フラグ  
 このフラグを使用して、 [SccPopulateList](../extensibility/sccpopulatelist-function.md)で、`fOptions`パラメーター。  
  
|フラグ|値|説明|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|IDE がファイルではなく、ディレクトリを渡すことです。|  
  
## <a name="populatedirlist-flags"></a>PopulateDirList フラグ  
 これらのフラグを使用して、 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)で、`fOptions`パラメーター。  
  
|オプションの値|[値]|説明|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|(これは、既定値) のディレクトリのディレクトリの 1 つだけのレベルを確認します。|  
|SCC_PDL_RECURSIVE|0x0001|再帰的には、各指定したディレクトリの下のすべてのディレクトリを確認します。|  
|SCC_PDL_INCLUDEFILES|0x0002|検査プロセスでファイル名が含まれます。|  
  
## <a name="openproject-flags"></a>プロジェクトを開くフラグ  
 これらのフラグを使用して、 [SccOpenProject](../extensibility/sccopenproject-function.md)で、`dwFlags`パラメーター。  
  
|オプションの値|[値]|説明|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|ソース管理にプロジェクトが存在しない場合は、それを作成します。 このフラグが設定されていないプロジェクトを作成するには、ユーザーの入力を求める (しない限り、`SCC_OP_SILENTOPEN`フラグを指定)。|  
|SCC_OP_SILENTOPEN|0x00000002L|プロジェクトを作成するユーザーに確認しません。戻り値`SCC_E_UNKNOWNPROJECT`です。|  
  
## <a name="get-flags"></a>フラグを取得します。  
 これらのフラグを使用して、 [SccGet](../extensibility/sccget-function.md)と[SccCheckout](../extensibility/scccheckout-function.md)です。  
  
|フラグ|値|説明|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|IDE のディレクトリを渡すことは、ファイルではありません。 これらのディレクトリ内のすべてのファイルを取得します。|  
|`SCC_GET_RECURSIVE`|0x00000002L|IDE がディレクトリに渡す: これらのディレクトリとそのすべてのサブディレクトリを取得します。|  
  
## <a name="noption-values"></a>nOption 値  
 これらのフラグを使用して、 [SccSetOption](../extensibility/sccsetoption-function.md)で、`nOption`パラメーター。  
  
|フラグ|値|説明|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|イベント キューの状態を設定します。|  
|`SCC_OPT_USERDATA`|0x00000002L|ユーザーのデータの指定`SCC_OPT_NAMECHANGEPFN`です。|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE は、[キャンセル] を処理できます。|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|名前の変更のコールバックを設定します。|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|ソース管理のプラグイン UI チェック アウトを無効にし、作業ディレクトリを設定しないでください。|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|作業ディレクトリを指定するソース管理システムから追加します。 直接の子孫である場合、関連付けられているプロジェクトに共有しようとしてください。|  
  
## <a name="dwval-bitflags"></a>dwVal ビットフラグ  
 これらのフラグを使用して、 [SccSetOption](../extensibility/sccsetoption-function.md)で、`dwVal`パラメーター。  
  
|フラグ|値|説明|によって使用される`nOption`値|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|イベント キューのアクティビティを中断します。|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|イベント キューのログ記録を有効にします。|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(既定値)[キャンセル] モードがありません。プラグインが必要必要な場合です。|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1 L|IDE では、[キャンセル] を処理します。|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(既定値)プラグインの UI からチェック アウトするには、[ok]作業ディレクトリを設定します。|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1 L|ないプラグインの UI のチェック アウトは、作業ディレクトリはありません。|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)