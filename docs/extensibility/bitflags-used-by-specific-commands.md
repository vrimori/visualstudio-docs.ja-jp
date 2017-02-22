---
title: "特定のコマンドで使用されるビットフラグ | Microsoft Docs"
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
  - "ソース管理プラグインを特定のコマンドで使用されるビットフラグ"
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# 特定のコマンドで使用されるビットフラグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

1 つの値の 1 つまたは複数のビットを設定して、さまざまなソース管理プラグインの API の関数の動作を変更できます。 これらの値は、ビットフラグと呼ばれます。 ソース管理プラグインの API で使用されるさまざまなビットフラグ詳細についてはここでは、それらを使用する関数ごとにグループ化します。  
  
## チェック アウト フラグ  
 このフラグは、いずれかに設定することができます、 [SccAdd](../extensibility/sccadd-function.md) または [SccCheckin](../extensibility/scccheckin-function.md)です。  
  
|フラグ|値|説明|  
|---------|-------|--------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|ファイルをチェック アウトしてください。|  
  
## フラグを追加します。  
 これらのフラグが使用される、 [SccAdd](../extensibility/sccadd-function.md)です。  
  
|フラグ|値|説明|  
|---------|-------|--------|  
|`SCC_FILETYPE_AUTO`|0x00|ファイルがテキストかバイナリかどうかを自動的に検出するには、ソース管理プラグインが必要です。|  
|`SCC_FILETYPE_TEXT`|0x01|ファイルの種類は、テキストです。|  
|`SCC_FILETYPE_BINARY`|0x04|ファイルの種類はバイナリです。 **Note:**  `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` フラグは相互に排他的です。 1 つだけ、またはどちらも設定します。|  
|`SCC_ADD_STORELATEST`|0x02|最新のバージョンのみ \(デルタなし\) を格納します。|  
  
## 比較フラグ  
 [SccDiff](../extensibility/sccdiff-function.md) これらのフラグを使用して、diff 操作のスコープを定義します。`SCC_DIFF_QD_xxx` フラグは相互に排他的です。 いずれかのファイルが指定されている場合、視覚的なフィードバックはありません付与します。 「クイック比較」に \(QD\) プラグインによって決定されないか、ファイルは異なりますが異なる場合のみです。 これらのフラグを指定した場合のいずれも、「visual 比較」を実行します。詳細なファイルの相違点が計算され、表示されます。 要求された QD はサポートされていない場合、プラグインが、次の最良の提案に移動します。 たとえば、IDE、チェックサムの要求プラグインはサポートされていない場合は、プラグインは全内容を確認 \(まだよりもかなり速くがビジュアルに表示\) します。  
  
|フラグ|値|説明|  
|---------|-------|--------|  
|`SCC_DIFF_IGNORECASE`|0x0002|小文字の相違を無視します。|  
|`SCC_DIFF_IGNORESPACE`|0x0004|空白の相違を無視します。 **Note:**  `SCC_DIFF_IGNORECASE` と `SCC_DIFF_IGNORESPACE` フラグは省略可能なビットフラグです。|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|ファイルの内容全体を比較することによって QD します。|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|チェックサムによって QD します。|  
|`SCC_DIFF_QD_TIME`|0x0040|ファイルの日付\/時刻スタンプによって QD します。|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|これは、すべての QD ビットフラグの確認に使用されるマスクです。 渡すことはできません。 関数に次の 3 つの QD ビットフラグは相互に排他的です。 QD には、UI の表示を常に意味するものはありません。|  
  
## PopulateList フラグ  
 このフラグを使用して、 [SccPopulateList](../extensibility/sccpopulatelist-function.md) で、 `fOptions` パラメーター。  
  
|フラグ|値|説明|  
|---------|-------|--------|  
|`SCC_PL_DIR`|0x00000001L|IDE はファイルではなく、ディレクトリを合格しています。|  
  
## PopulateDirList フラグ  
 これらのフラグが使用される、 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) で、 `fOptions` パラメーター。  
  
|オプションの値|値|説明|  
|-------------|-------|--------|  
|SCC\_PDL\_ONELEVEL|0x0000|\(これは、既定値\) のディレクトリのディレクトリの 1 つだけのレベルを確認します。|  
|SCC\_PDL\_RECURSIVE|0x0001|再帰的には、指定された各ディレクトリの下のすべてのディレクトリを確認します。|  
|SCC\_PDL\_INCLUDEFILES|0x0002|検証プロセスでファイル名が含まれます。|  
  
## プロジェクトを開くフラグ  
 これらのフラグが使用される、 [SccOpenProject](../extensibility/sccopenproject-function.md) で、 `dwFlags` パラメーター。  
  
|オプションの値|値|説明|  
|-------------|-------|--------|  
|SCC\_OP\_CREATEIFNEW|0x00000001L|ソース管理にプロジェクトが存在しない場合は作成します。 このフラグが設定されていない場合は、プロジェクトのユーザーが作成を求めるメッセージ \(しない限り、 `SCC_OP_SILENTOPEN` フラグが指定されている\)。|  
|SCC\_OP\_SILENTOPEN|0x00000002L|ダイアログを表示しません。 プロジェクトを作成するユーザー戻り値 `SCC_E_UNKNOWNPROJECT`です。|  
  
## フラグを取得します。  
 これらのフラグが使用される、 [SccGet](../extensibility/sccget-function.md) と [SccCheckout](../extensibility/scccheckout-function.md)です。  
  
|フラグ|値|説明|  
|---------|-------|--------|  
|`SCC_GET_ALL`|0x00000001L|IDE が渡されたディレクトリ、ファイルではありません。 これらのディレクトリ内のすべてのファイルを取得します。|  
|`SCC_GET_RECURSIVE`|0x00000002L|IDE が渡されたディレクトリ: これらのディレクトリとそのすべてのサブディレクトリを取得します。|  
  
## nOption 値  
 これらのフラグが使用される、 [SccSetOption](../extensibility/sccsetoption-function.md) で、 `nOption` パラメーター。  
  
|フラグ|値|説明|  
|---------|-------|--------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|イベント キューの状態を設定します。|  
|`SCC_OPT_USERDATA`|0x00000002L|ユーザー データの指定 `SCC_OPT_NAMECHANGEPFN`します。|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE は、\[キャンセル\] を処理できます。|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|名前の変更のコールバックを設定します。|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|ソース管理のプラグイン UI チェック アウトを無効にして、作業ディレクトリを設定しないでください。|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|作業ディレクトリを指定するソース管理システムから追加します。 直接の子孫である場合に関連付けられているプロジェクトを共有しようとしてください。|  
  
## dwVal ビットフラグ  
 これらのフラグが使用される、 [SccSetOption](../extensibility/sccsetoption-function.md) で、 `dwVal` パラメーター。  
  
|フラグ|値|説明|使用される `nOption` 値|  
|---------|-------|--------|-----------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|イベント キューのアクティビティを中断します。|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|イベント キューのログ記録を有効にします。|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0 L|\(既定値\)\[キャンセル\] モードがありません。プラグインが必要が必要な場合です。|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1 L|IDE では、\[キャンセル\] を処理します。|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0 L|\(既定値\)プラグインの UI からチェック アウトするには、\[ok\]作業ディレクトリを設定します。|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1 L|ないプラグインの UI のチェック アウト、作業ディレクトリはありません。|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## 参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)