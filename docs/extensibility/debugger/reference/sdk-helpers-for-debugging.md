---
title: デバッグ用の SDK ヘルパー |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d352e22b95540cfc1901eb214c2d5180b6024f27
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821527"
---
# <a name="sdk-helpers-for-debugging"></a>デバッグ用の SDK ヘルパー
これらの関数と宣言は、C++ でのデバッグ エンジン、式エバリュエーターでは、およびシンボル プロバイダーを実装するためのグローバルなヘルパー関数です。  
  
> [!NOTE]
>  この時点では、これらの関数と宣言のマネージ バージョンはありません。  
  
## <a name="overview"></a>概要  
 Visual Studio で使用するデバッグ エンジン、式エバリュエーターでは、およびシンボル プロバイダーの順序でこれらを登録する必要があります。 これは、レジストリ サブキーとエントリ、それ以外の場合は「メトリックを設定します」と呼ばれる設定で 次のグローバル関数は、これらのメトリックの更新のプロセスを容易に設計されています。 これらの関数によって更新される各レジストリ サブキーのレイアウトを確認するレジストリの場所に、セクションを参照してください。  
  
## <a name="general-metric-functions"></a>一般的なメトリック関数  
 これらは、デバッグ エンジンで使用される一般的な関数です。 式エバリュエーターの関数に特化したし、シンボル プロバイダーが後で詳しく説明します。  
  
### <a name="getmetric-method"></a>GetMetric メソッド  
 レジストリからのメトリックの値を取得します。  
  
```cpp  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|パラメーター|説明|  
|---------------|-----------------|  
|pszMachine|[in]登録が書き込まれる可能性があるリモート コンピューターの名前 (`NULL`ローカル コンピューターのことを意味する)。|  
|pszType|[in]メトリックの種類のいずれか。|  
|guidSection|[in]特定のエンジン、エバリュエーター、例外などの GUID です。これには、メトリックの種類の特定の要素の下のサブセクションを指定します。|  
|pszMetric|[in]メトリックを取得できます。 これは、特定の値の名前に対応します。|  
|pdwValue|[in]メトリックの値の格納場所。 (この例では) のように、DWORD、BSTR、GUID または Guid の配列を返すことができる GetMetric の一部のエディションがあります。|  
|pszAltRoot|[in]使用する別のレジストリ ルート。 設定`NULL`既定値を使用します。|  
  
### <a name="setmetric-method"></a>SetMetric メソッド  
 レジストリで指定したメトリックの値を設定します。  
  
```cpp  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|パラメーター|説明|  
|---------------|-----------------|  
|pszType|[in]メトリックの種類のいずれか。|  
|guidSection|[in]特定のエンジン、エバリュエーター、例外などの GUID です。これには、メトリックの種類の特定の要素の下のサブセクションを指定します。|  
|pszMetric|[in]メトリックを取得できます。 これは、特定の値の名前に対応します。|  
|dwValue|[in]メトリックの値の格納場所。 (この例では) で DWORD、BSTR、GUID または Guid の配列に格納できる SetMetric の一部のエディションがあります。|  
|fUserSpecific|[in]TRUE のメトリックがユーザーに固有である場合や、ローカル マシン ハイブではなく、ユーザーのハイブに書き込む必要があります。|  
|pszAltRoot|[in]使用する別のレジストリ ルート。 設定`NULL`既定値を使用します。|  
  
### <a name="removemetric-method"></a>RemoveMetric メソッド  
 レジストリから指定したメトリックを削除します。  
  
```cpp  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|パラメーター|説明|  
|---------------|-----------------|  
|pszType|[in]メトリックの種類のいずれか。|  
|guidSection|[in]特定のエンジン、エバリュエーター、例外などの GUID です。これには、メトリックの種類の特定の要素の下のサブセクションを指定します。|  
|pszMetric|[in]削除するメトリック。 これは、特定の値の名前に対応します。|  
|pszAltRoot|[in]使用する別のレジストリ ルート。 設定`NULL`既定値を使用します。|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections メソッド  
 レジストリのさまざまなメトリックのセクションを列挙します。  
  
```cpp  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|パラメーター|説明|  
|---------------|-----------------|  
|pszMachine|[in]登録が書き込まれる可能性があるリモート コンピューターの名前 (`NULL`ローカル コンピューターのことを意味する)。|  
|pszType|[in]メトリックの種類のいずれか。|  
|rgguidSections|[入力、出力]情報を格納する Guid を事前に割り当てられた配列。|  
|pdwSize|[in]格納できる Guid の最大数、`rgguidSections`配列。|  
|pszAltRoot|[in]使用する別のレジストリ ルート。 設定`NULL`既定値を使用します。|  
  
## <a name="expression-evaluator-functions"></a>式エバリュエーターの関数  
  
|関数|説明|  
|--------------|-----------------|  
|GetEEMetric|レジストリからのメトリックの値を取得します。|  
|SetEEMetric|レジストリで指定したメトリックの値を設定します。|  
|RemoveEEMetric|レジストリから指定したメトリックを削除します。|  
|GetEEMetricFile|指定したメトリックからファイル名を取得し、ファイルの内容を文字列として返す、読み込みます。|  
  
## <a name="exception-functions"></a>例外関数  
  
|関数|説明|  
|--------------|-----------------|  
|GetExceptionMetric|レジストリからのメトリックの値を取得します。|  
|SetExceptionMetric|レジストリで指定したメトリックの値を設定します。|  
|RemoveExceptionMetric|レジストリから指定したメトリックを削除します。|  
|RemoveAllExceptionMetrics|レジストリからすべての例外のメトリックを削除します。|  
  
## <a name="symbol-provider-functions"></a>シンボル プロバイダー関数  
  
|関数|説明|  
|--------------|-----------------|  
|GetSPMetric|レジストリからのメトリックの値を取得します。|  
|SetSPMetric|レジストリで指定したメトリックの値を設定します。|  
|RemoveSPMetric|レジストリから指定したメトリックを削除します。|  
  
## <a name="enumeration-functions"></a>列挙関数  
  
|関数|説明|  
|--------------|-----------------|  
|EnumMetricSections|指定したメトリックの種類のすべてのメトリックを列挙します。|  
|EnumDebugEngine|登録済みのデバッグ エンジンを列挙します。|  
|EnumEEs|登録済みの式エバリュエーターを列挙します。|  
|EnumExceptionMetrics|例外のすべてのメトリックを列挙します。|  
  
## <a name="metric-definitions"></a>メトリック定義  
 これらの定義は、定義済みのメトリック名は使用できます。 名前はさまざまなレジストリ キーと値の名前とワイド文字の文字列として定義されているがすべてに対応します。 たとえば、 `extern LPCWSTR metrictypeEngine`。  
  
|定義済みのメトリックの種類|説明: の基本キー.|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|すべてのデバッグ エンジンのメトリック。|  
|metrictypePortSupplier|すべてのポート サプライヤー メトリック。|  
|metrictypeException|すべての例外のメトリック。|  
|metricttypeEEExtension|すべての式エバリュエーターの拡張機能。|  
  
|デバッグ エンジン プロパティ|説明|  
|-----------------------------|-----------------|  
|metricAddressBP|アドレスのブレークポイントのサポートを示す 0 以外の値に設定します。|  
|metricAlwaysLoadLocal|常にローカルにデバッグ エンジンを読み込むためには 0 以外の値に設定します。|  
|metricLoadInDebuggeeSession|使用されていません|  
|metricLoadedByDebuggee|示す、またはデバッグ中のプログラムでは、デバッグ エンジンを読み込む常には 0 以外の値に設定します。|  
|metricAttach|既存のプログラムに添付ファイルのサポートを示す 0 以外の値に設定します。|  
|metricCallStackBP|呼び出し履歴のブレークポイントのサポートを示す 0 以外の値に設定します。|  
|metricConditionalBP|条件付きブレークポイントの設定のサポートを示す 0 以外の値に設定します。|  
|metricDataBP|データの変更のブレークポイントの設定のサポートを示す 0 以外の値に設定します。|  
|metricDisassembly|[逆アセンブル] 一覧の運用環境のサポートを示すために 0 以外の値を設定します。|  
|metricDumpWriting|ダンプの書き込み (ダンプの出力デバイスへのメモリ) のサポートを示す 0 以外の値に設定します。|  
|metricENC|エディット コンティニュのサポートを示すために 0 以外の値を設定します。 **注:** カスタム デバッグ エンジンはこれを設定する必要がありますしないまたは 0 に設定常にする必要があります。|  
|metricExceptions|例外のサポートを示す 0 以外の値に設定します。|  
|metricFunctionBP|名前付きブレークポイント (を特定の関数名が呼び出されたときに中断するブレークポイント) のサポートを示す 0 以外の値に設定します。|  
|metricHitCountBP|「ポイントをヒット」ブレークポイント (一定回数がヒットされている後にのみトリガーされるブレークポイント) の設定のサポートを示す 0 以外の値に設定します。|  
|metricJITDebug|ジャストイン タイムのデバッグ (デバッガーは実行中のプロセスで例外が発生したときに起動される) のサポートを示すために 0 以外の値を設定します。|  
|metricMemory|使用されていません|  
|metricPortSupplier|1 つを実装する場合、ポート サプライヤーの CLSID を設定します。|  
|metricRegisters|使用されていません|  
|metricSetNextStatement|(これは、中間のステートメントの実行をスキップします)、次のステートメントを設定するためのサポートを示すために 0 以外に設定します。|  
|metricSuspendThread|スレッド実行の中断のサポートを示す 0 以外の値に設定します。|  
|metricWarnIfNoSymbols|シンボルがない場合、ユーザーに通知することを示す 0 以外の値に設定します。|  
|metricProgramProvider|これは、プログラムのプロバイダーの CLSID を設定します。|  
|metricAlwaysLoadProgramProviderLocal|0 以外にすることを示すプログラム プロバイダーは常に読み込まれたローカルに設定します。|  
|metricEngineCanWatchProcess|これを設定を示すプログラム プロバイダーではなくプロセス イベント デバッグ エンジンの監視は、0 以外の値。|  
|metricRemoteDebugging|これ 0 以外に設定をリモート デバッグのサポートを示します。|  
|metricEncUseNativeBuilder|この設定を示す、編集と続行マネージャー使用すること、デバッグ エンジンの encbuild.dll エディット コンティニュ用にビルドするには 0 以外の値。 **注:** カスタム デバッグ エンジンはこれを設定する必要がありますしないまたは 0 に設定常にする必要があります。|  
|metricLoadUnderWOW64|これ 0 以外に設定を示す、64 ビット プロセスをデバッグするときに、WOW の下で、デバッグ対象プロセスで、デバッグ エンジンを読み込む必要があります。それ以外の場合、デバッグ エンジンは、(WOW64 の下で実行されている) を Visual Studio のプロセスに読み込まれます。|  
|metricLoadProgramProviderUnderWOW64|これ 0 以外に設定; WOW の下で、64 ビット プロセスをデバッグするときに、プログラムのプロバイダーがデバッグ対象プロセスに読み込まれたをするにはそれ以外の場合、Visual Studio のプロセスで読み込まれます。|  
|metricStopOnExceptionCrossingManagedBoundary|これ 0 以外に設定を示すマネージ/アンマネージ コードの境界を越えて、未処理の例外がスローされた場合、プロセスを停止します。|  
|metricAutoSelectPriority|デバッグ エンジン (より高い値と等しいより高い優先度) の自動選択の優先順位を設定します。|  
|metricAutoSelectIncompatibleList|レジストリ キーがで自動選択が無視されるデバッグ エンジンの Guid を指定するエントリが格納されます。 これらのエントリは、数 (0、1、2、およびなど) を文字列として表される GUID を使用します。|  
|metricIncompatibleList|このデバッグ エンジンと互換性のないデバッグ エンジンの Guid を指定するエントリを含むレジストリ キー。|  
|metricDisableJITOptimization|これ 0 以外に設定をデバッグ中に (マネージ コード) のジャストイン タイムの最適化を無効にすることを示します。|  
  
|式エバリュエーターのプロパティ|説明|  
|-------------------------------------|-----------------|  
|metricEngine|これは、指定された式エバリュエーターをサポートするデバッグ エンジンの数を保持します。|  
|metricPreloadModules|これを設定、式エバリュエーターが、プログラムに対して起動されるとき、モジュールをプリロードするかを示す 0 以外の値。|  
|metricThisObjectName|"This"オブジェクトの名前を設定します。|  
  
|式エバリュエーターの拡張機能プロパティ|説明|  
| - |-----------------|  
|metricExtensionDll|この拡張機能をサポートしている dll の名前です。|  
|metricExtensionRegistersSupported|サポートされているレジスタの一覧です。|  
|metricExtensionRegistersEntryPoint|レジスタへのアクセスのエントリ ポイント。|  
|metricExtensionTypesSupported|サポートされている種類の一覧です。|  
|metricExtensionTypesEntryPoint|型へのアクセスのエントリ ポイント。|  
  
|ポート サプライヤーのプロパティ|説明|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|(ポートを選択し、デバッグに使用するポートを追加する ダイアログ ボックス、ユーザーが使用できます) ポートの選択コントロールの CLSID。|  
|metricDisallowUserEnteredPorts|ポート サプライヤーにユーザーが入力したポートを追加できない場合、0 以外の場合 (これにより、ポートの選択 ダイアログ ボックス本質的に読み取り専用)。|  
|metricPidBase|プロセス Id を割り当てるときに、ポート サプライヤーで使用される基本のプロセス ID。|  
  
|定義済みの SP ストアの種類|説明|  
|-------------------------------|-----------------|  
|storetypeFile|シンボルは、別のファイルに格納されます。|  
|storetypeMetadata|シンボルは、アセンブリ内のメタデータとして格納されます。|  
  
|その他のプロパティ|説明|  
|------------------------------|-----------------|  
|metricShowNonUserCode|これ 0 以外に設定を非ユーザー コードを表示します。|  
|metricJustMyCodeStepping|これ 0 以外に設定をステップ実行がユーザー コードでのみ発生することことを示します。|  
|metricCLSID|特定のメトリックの種類のオブジェクトの CLSID。|  
|MetricName|特定のメトリックの種類のオブジェクトのわかりやすい名前。|  
|metricLanguage|言語の名前。|  
  
## <a name="registry-locations"></a>レジストリの場所  
 メトリックを読み取ったりで具体的には、レジストリに書き込まれた、`VisualStudio`サブキー。  
  
> [!NOTE]
>  ほとんどの場合、メトリックは、HKEY_LOCAL_MACHINE キーに書き込まれます。 ただし、場合によって HKEY_CURRENT_USER キーになります、変換先。 Dbgmetric.lib では、両方のキーを処理します。 メトリックを取得するには、HKEY_CURRENT_USER が検索してから、HKEY_LOCAL_MACHINE。 メトリックを設定していることは、パラメーターは、最上位レベルを使用するキーを指定します。  
  
 *[レジストリ キー]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[バージョン root]*\  
  
 *[メトリックの root]*\  
  
 *[メトリックの種類]*\  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[レジストリ キー]*|`HKEY_CURRENT_USER` または `HKEY_LOCAL_MACHINE`。|  
|*[バージョン root]*|Visual Studio のバージョン (たとえば、 `7.0`、 `7.1`、または`8.0`)。 ただし、このルート変更することもを使用して、 **/rootsuffix**に切り替える**devenv.exe**します。 VSIP、この修飾子は通常**Exp**バージョン ルートである場合は、たとえば 8.0Exp のため、します。|  
|*[メトリックの root]*|いずれかになります`AD7Metrics`または`AD7Metrics(Debug)`dbgmetric.lib のデバッグ バージョンを使用するかどうかに応じて、します。 **注:** デバッグとリリースの違いがある場合、この名前付け規則に従う必要があります dbgmetric.lib を使用すると、かどうかのバージョンをレジストリに反映する必要があります。|  
|*[メトリックの種類]*|書き込まれるメトリックの種類: `Engine`、 `ExpressionEvaluator`、`SymbolProvider`など。これらすべてとして dbgmetric.h のように定義されます`metricTypeXXXX`ここで、`XXXX`は特定の種類の名前です。|  
|*[メトリック]*|メトリックを設定するには値を代入するエントリの名前。 メトリックの実際の組織は、メトリックの種類によって異なります。|  
|*[メトリックの値]*|メトリックに割り当てられた値。 型の値 (文字列、数値など) が必要では、メトリックに依存します。|  
  
> [!NOTE]
>  すべての Guid がの形式で格納されている`{GUID}`します。 たとえば、`{123D150B-FA18-461C-B218-45B3E4589F9B}` のようにします。  
  
### <a name="debug-engines"></a>デバッグ エンジン  
 レジストリでのデバッグ エンジンのメトリックの構成を次に示します。 `Engine` デバッグ エンジンのメトリックの種類の名前に対応して *[メトリックの種類]* 上記のレジストリ サブツリーでします。  
  
 `Engine`\  
  
 *[エンジン guid]*\  
  
 `CLSID` = *[クラス guid]*  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
 `PortSupplier`\  
  
 `0` = *[ポートのサプライヤーの guid]*  
  
 `1` = *[ポートのサプライヤーの guid]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[エンジン guid]*|デバッグ エンジンの GUID です。|  
|*[クラス guid]*|このデバッグ エンジンを実装するクラスの GUID です。|  
|*[ポートのサプライヤーの guid]*|存在する場合は、ポートのサプライヤーの GUID です。 多数のデバッグ エンジンでは、既定のポート サプライヤーの使用し、独自の仕入先を指定しません。 この場合は、サブキー`PortSupplier`は表示されません。|  
  
### <a name="port-suppliers"></a>ポート サプライヤー  
 レジストリ内のポート サプライヤー メトリックの構成を次に示します。 `PortSupplier` ポート サプライヤーのメトリックの種類の名前に対応して *[メトリックの種類]* します。  
  
 `PortSupplier`\  
  
 *[ポートのサプライヤーの guid]*\  
  
 `CLSID` = *[クラス guid]*  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[ポートのサプライヤーの guid]*|ポート サプライヤーの GUID|  
|*[クラス guid]*|このポートのサプライヤーを実装するクラスの GUID|  
  
### <a name="symbol-providers"></a>シンボル プロバイダー  
 レジストリ内のシンボル サプライヤー メトリックの構成を次に示します。 `SymbolProvider` シンボル プロバイダーのメトリックの種類の名前に対応して *[メトリックの種類]* します。  
  
 `SymbolProvider`\  
  
 *[シンボル プロバイダー guid]*\  
  
 `file`\  
  
 `CLSID` = *[クラス guid]*  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
 `metadata`\  
  
 `CLSID` = *[クラス guid]*  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[シンボル プロバイダー guid]*|シンボル プロバイダーの GUID|  
|*[クラス guid]*|このシンボル プロバイダーを実装するクラスの GUID|  
  
### <a name="expression-evaluators"></a>式エバリュエーター  
 レジストリで、式エバリュエーターのメトリックの構成を次に示します。 `ExpressionEvaluator` 式エバリュエーターのメトリックの種類の名前に対応して *[メトリックの種類]* します。  
  
> [!NOTE]
>  メトリックの種類の`ExpressionEvaluator`式エバリュエーターのメトリックの変更がすべてが適切な式エバリュエーターのメトリック関数を使用して送られることが前提として、dbgmetric.h で定義されていない (のレイアウト、`ExpressionEvaluator`サブキーがいくらか複雑な詳細は dbgmetric.lib 内部に隠されたため)。  
  
 `ExpressionEvaluator`\  
  
 *[言語の guid]*\  
  
 *[ベンダー guid]*\  
  
 `CLSID` = *[クラス guid]*  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
 `Engine`\  
  
 `0` = *[デバッグ エンジンの guid]*  
  
 `1` = *[デバッグ エンジンの guid]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[言語の guid]*|言語の GUID|  
|*[ベンダー guid]*|仕入先の GUID|  
|*[クラス guid]*|この式エバリュエーターを実装するクラスの GUID|  
|*[デバッグ エンジンの guid]*|この式エバリュエーターが連携するデバッグ エンジンの GUID|  
  
### <a name="expression-evaluator-extensions"></a>式エバリュエーターの拡張機能  
 レジストリ内の式エバリュエーター拡張メトリックの構成を次に示します。 `EEExtensions` エバリュエーターの拡張機能は、式のメトリックの種類の名前に対応して *[メトリックの種類]* します。  
  
 `EEExtensions`\  
  
 *[拡張機能の guid]*\  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[拡張機能の guid]*|式エバリュエーターの拡張機能の GUID|  
  
### <a name="exceptions"></a>例外  
 レジストリの例外のメトリックの構成を次に示します。 `Exception` 例外のメトリックの種類の名前に対応して *[メトリックの種類]* します。  
  
 `Exception`\  
  
 *[デバッグ エンジンの guid]*\  
  
 *[例外の種類]*\  
  
 *[例外]*\  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
 *[例外]*\  
  
 *[メトリック] = [メトリックの値]*  
  
 *[メトリック] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[デバッグ エンジンの guid]*|例外をサポートするデバッグ エンジンの GUID です。|  
|*[例外の種類]*|処理できる例外のクラスを識別するサブキーの一般的なタイトルです。 一般的な名前は**C++ 例外**、 **Win32 例外**、 **Common Language Runtime Exceptions**、および**ネイティブ ランタイム チェック**します。 これらの名前は、ユーザーに例外の特定のクラスを識別するためにも使用されます。|  
|*[例外]*|例外の名前。 たとえば、 **_com_error**または**コントロール ブレーク**します。 これらの名前は、ユーザーに特定の例外を識別するためにも使用されます。|  
  
## <a name="requirements"></a>必要条件  
 これらのファイルにある、 [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK のインストール ディレクトリ (既定では、 *[ドライブ]* \Program Files\Microsoft Visual Studio 2010 SDK\\)。  
  
 ヘッダー: includes\dbgmetric.h  
  
 ライブラリ: libs\ad2de.lib、libs\dbgmetric.lib  
  
## <a name="see-also"></a>関連項目  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)