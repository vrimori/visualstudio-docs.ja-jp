---
title: "デバッグ用の SDK ヘルパー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b87756f52cb1506be30014331d63eec5d15beff4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sdk-helpers-for-debugging"></a>デバッグ用の SDK ヘルパー
これらの関数と宣言は、C++ でのデバッグ エンジン、式の評価者、およびシンボル プロバイダーを実装するためのグローバルなヘルパー関数です。  
  
> [!NOTE]
>  この時点では、これらの関数と宣言の管理対象のバージョンはありません。  
  
## <a name="overview"></a>概要  
 Visual Studio で使用するデバッグ エンジン、式の評価者、およびシンボル プロバイダーの順序でこれらを登録してください。 これは、レジストリ サブキーとエントリ、それ以外の場合「メトリックを設定します」と呼ばれる設定で 次のグローバル関数は、これらのメトリックを更新するプロセスを容易に設計されています。 これらの関数によって更新される各レジストリ サブキーのレイアウトを確認するレジストリの場所には、セクションを参照してください。  
  
## <a name="general-metric-functions"></a>一般的なメトリック関数  
 これらは、デバッグ エンジンで使用される一般的な機能です。 式エバリュエーターの関数に特殊化し、プロバイダーのシンボルが後で詳しく説明します。  
  
### <a name="getmetric-method"></a>GetMetric メソッド  
 レジストリからメトリックの値を取得します。  
  
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
|pszMachine|[in]レジスタが書き込まれる可能性のあるリモート コンピューターの名前 (`NULL`ローカル コンピューターのことを意味する)。|  
|pszType|[in]メトリックの種類のいずれか。|  
|guidSection|[in]特定のエンジン、エバリュエーター、例外などの GUID です。これには、特定の要素のメトリックの種類の下のサブセクションを指定します。|  
|pszMetric|[in]取得するメトリックです。 これは、特定の値の名前に対応します。|  
|pdwValue|[in]メトリックの値の格納場所。 (この例では) のように DWORD、BSTR、GUID、または Guid の配列を返すことができる GetMetric の一部のエディションがあります。|  
|pszAltRoot|[in]使用する別のレジストリ ルート。 設定`NULL`既定値を使用します。|  
  
### <a name="setmetric-method"></a>SetMetric メソッド  
 レジストリで指定されたメトリックの値を設定します。  
  
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
|guidSection|[in]特定のエンジン、エバリュエーター、例外などの GUID です。これには、特定の要素のメトリックの種類の下のサブセクションを指定します。|  
|pszMetric|[in]取得するメトリックです。 これは、特定の値の名前に対応します。|  
|dwValue|[in]メトリックの値の格納場所。 (この例では) では、DWORD、BSTR、GUID、または Guid の配列に格納できる SetMetric の一部のエディションがあります。|  
|fUserSpecific|[in]TRUE のメトリックがユーザーに固有である場合や、ローカル マシン ハイブではなく、ユーザーのハイブに書き込む必要があります。|  
|pszAltRoot|[in]使用する別のレジストリ ルート。 設定`NULL`既定値を使用します。|  
  
### <a name="removemetric-method"></a>RemoveMetric メソッド  
 レジストリから指定されたメトリックを削除します。  
  
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
|guidSection|[in]特定のエンジン、エバリュエーター、例外などの GUID です。これには、特定の要素のメトリックの種類の下のサブセクションを指定します。|  
|pszMetric|[in]削除するメトリックです。 これは、特定の値の名前に対応します。|  
|pszAltRoot|[in]使用する別のレジストリ ルート。 設定`NULL`既定値を使用します。|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections メソッド  
 さまざまなメトリック セクションでは、レジストリを列挙します。  
  
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
|pszMachine|[in]レジスタが書き込まれる可能性のあるリモート コンピューターの名前 (`NULL`ローカル コンピューターのことを意味する)。|  
|pszType|[in]メトリックの種類のいずれか。|  
|rgguidSections|[入力、出力].格納される Guid の事前に割り当てられた配列。|  
|pdwSize|[in]格納できる Guid の最大数、`rgguidSections`配列。|  
|pszAltRoot|[in]使用する別のレジストリ ルート。 設定`NULL`既定値を使用します。|  
  
## <a name="expression-evaluator-functions"></a>式エバリュエーター機能  
  
|関数|説明|  
|--------------|-----------------|  
|GetEEMetric|レジストリからメトリックの値を取得します。|  
|SetEEMetric|レジストリで指定されたメトリックの値を設定します。|  
|RemoveEEMetric|レジストリから指定されたメトリックを削除します。|  
|GetEEMetricFile|指定されたメトリックからファイル名を取得し、ファイルの内容を文字列として返す、読み込みます。|  
  
## <a name="exception-functions"></a>例外関数  
  
|関数|説明|  
|--------------|-----------------|  
|GetExceptionMetric|レジストリからメトリックの値を取得します。|  
|SetExceptionMetric|レジストリで指定されたメトリックの値を設定します。|  
|RemoveExceptionMetric|レジストリから指定されたメトリックを削除します。|  
|RemoveAllExceptionMetrics|レジストリからすべての例外のメトリックを削除します。|  
  
## <a name="symbol-provider-functions"></a>シンボル プロバイダー関数  
  
|関数|説明|  
|--------------|-----------------|  
|GetSPMetric|レジストリからメトリックの値を取得します。|  
|SetSPMetric|レジストリで指定されたメトリックの値を設定します。|  
|RemoveSPMetric|レジストリから指定されたメトリックを削除します。|  
  
## <a name="enumeration-functions"></a>列挙関数  
  
|関数|説明|  
|--------------|-----------------|  
|EnumMetricSections|指定された指標の種類のすべてのメトリックを列挙します。|  
|EnumDebugEngine|登録されているデバッグ エンジンを列挙します。|  
|EnumEEs|登録済みの式エバリュエーターを列挙します。|  
|EnumExceptionMetrics|すべての例外のメトリックを列挙します。|  
  
## <a name="metric-definitions"></a>メトリックの定義  
 これらの定義は、定義済みのメトリック名を使用できます。 名前はさまざまなレジストリ キーと値の名前とワイド文字列として定義されているがすべてに対応します。 たとえば、`extern LPCWSTR metrictypeEngine`です。  
  
|メトリックの定義済みの型|説明: 基本のキーをしています.|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|すべてのデバッグ エンジン メトリック。|  
|metrictypePortSupplier|すべてのポート業者メトリック。|  
|metrictypeException|すべての例外のメトリック。|  
|metricttypeEEExtension|すべての式エバリュエーターの拡張機能です。|  
  
|デバッグ エンジン プロパティ|説明|  
|-----------------------------|-----------------|  
|metricAddressBP|アドレスのブレークポイントのサポートを示すために 0 以外に設定します。|  
|metricAlwaysLoadLocal|常にローカルでデバッグ エンジンを読み込むために 0 以外に設定します。|  
|metricLoadInDebuggeeSession|使用しません|  
|metricLoadedByDebuggee|デバッグ エンジンは常に読み込むこと、またはデバッグ中のプログラムでを示すために 0 以外に設定します。|  
|metricAttach|既存のプログラムに添付ファイルのサポートを示すために 0 以外に設定します。|  
|metricCallStackBP|呼び出し履歴のブレークポイントのサポートを示すために 0 以外に設定します。|  
|metricConditionalBP|条件付きブレークポイントの設定のサポートを示すために 0 以外に設定します。|  
|metricDataBP|データの変更のブレークポイントの設定のサポートを示すために 0 以外に設定します。|  
|metricDisassembly|[逆アセンブル] の一覧の運用環境のサポートを示すために 0 以外に設定します。|  
|metricDumpWriting|ダンプ (ダンプの出力デバイス メモリ) を記述のサポートを示すために 0 以外に設定します。|  
|metricENC|エディット コンティニュのサポートを示すために 0 以外に設定します。 **注:**カスタム デバッグ エンジンは、これは設定しないでまたは常に 0 に設定します。|  
|metricExceptions|例外のサポートを示すために 0 以外に設定します。|  
|metricFunctionBP|名前付きのブレークポイント (特定の関数名が呼び出されるときに中断するブレークポイント) のサポートを示すために 0 以外に設定します。|  
|metricHitCountBP|「ポイントをヒット」ブレークポイント (される回数だけのヒット後にのみトリガーされるブレークポイント) の設定のサポートを示すために 0 以外に設定します。|  
|metricJITDebug|ジャスト イン タイムのデバッグ (デバッガーは実行中のプロセスで例外が発生したときの起動) のサポートを示すために 0 以外に設定します。|  
|metricMemory|使用しません|  
|metricPortSupplier|いずれかが実装された場合、ポート供給業者の CLSID を設定します。|  
|metricRegisters|使用しません|  
|metricSetNextStatement|(中級者向けのステートメントの実行をスキップ) を次のステートメントを設定するためのサポートを示すために 0 以外に設定します。|  
|metricSuspendThread|スレッドの実行を中断する前にサポートを示すために 0 以外に設定します。|  
|metricWarnIfNoSymbols|シンボルが存在しない場合、ユーザーに通知することを示すために 0 以外に設定します。|  
|metricProgramProvider|プログラムのプロバイダーの CLSID に設定します。|  
|metricAlwaysLoadProgramProviderLocal|0 以外を指定すること、プログラムのプロバイダーは常に読み込まれたローカルに設定します。|  
|metricEngineCanWatchProcess|これを設定プログラム プロバイダーではなくプロセス イベントは、デバッグ エンジンをウォッチことを示すために 0 以外の値。|  
|metricRemoteDebugging|これに設定をリモート デバッグのサポートを示す 0 以外の値。|  
|metricEncUseNativeBuilder|編集と続行マネージャーを使用するデバッグ エンジンの encbuild.dll エディット コンティニュ用にビルドするには 0 以外に設定します。 **注:**カスタム デバッグ エンジンは、これは設定しないでまたは常に 0 に設定します。|  
|metricLoadUnderWOW64|これを設定して、デバッグ エンジンを読み込むこと wow デバッグ対象のプロセスで 64 ビット プロセスをデバッグするときを示すためには 0 以外。それ以外の場合、デバッグ エンジンは、Visual Studio のプロセス (WOW64 の下で実行されている) に読み込まれます。|  
|metricLoadProgramProviderUnderWOW64|これを設定して wow; 64 ビット プロセスをデバッグするときにプログラム プロバイダーをデバッグ対象のプロセスに読み込まれている必要があるように指定する 0 以外の値それ以外の場合、Visual Studio プロセスに読み込まれます。|  
|metricStopOnExceptionCrossingManagedBoundary|これに設定をマネージ/アンマネージ コードの境界を越えて、未処理の例外がスローされた場合、プロセスを停止するかを示す 0 以外の値。|  
|metricAutoSelectPriority|デバッグ エンジン (より高い値 equals より高い優先度) の自動選択の優先順位を設定します。|  
|metricAutoSelectIncompatibleList|レジストリ キーが自動選択で無視するようにデバッグ エンジンの Guid を指定するエントリが格納されます。 これらのエントリが数値 (0、1、2、およびなど) を文字列として表される GUID を使用します。|  
|metricIncompatibleList|このデバッグ エンジンと互換性がないデバッグ エンジンの Guid を指定するエントリを含むレジストリ キー。|  
|metricDisableJITOptimization|これを設定デバッグ中に (マネージ コード) の・ イン タイムの最適化機能を無効にすることを示すために 0 以外の値。|  
  
|式エバリュエーターのプロパティ|説明|  
|-------------------------------------|-----------------|  
|metricEngine|これは、指定された式エバリュエーターをサポートするデバッグ エンジンの数を保持します。|  
|metricPreloadModules|これを設定、式エバリュエーターが、プログラムに対して起動されるときにモジュールをプリロードすることを示すために 0 以外の値。|  
|metricThisObjectName|"This"オブジェクトの名前を設定します。|  
  
|式エバリュエーターの拡張機能プロパティ|説明|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|この拡張機能をサポートする dll の名前です。|  
|metricExtensionRegistersSupported|サポートされているレジスタの一覧です。|  
|metricExtensionRegistersEntryPoint|レジスタへのアクセスのエントリ ポイント。|  
|metricExtensionTypesSupported|サポートされる型の一覧です。|  
|metricExtensionTypesEntryPoint|型へのアクセスのエントリ ポイント。|  
  
|ポート仕入先のプロパティ|説明|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|(ポートを選択し、デバッグに使用するポートを追加する ダイアログ ボックス、ユーザーが使用できます)、ポート ピッカーの CLSID。|  
|metricDisallowUserEnteredPorts|ユーザーが入力したポートをポートの仕入先を追加できない場合は 0 以外 (これにより、ポートの選択 ダイアログ ボックス本質的に読み取り専用)。|  
|metricPidBase|プロセス Id を割り当てるときに、ポート業者で使用される基本のプロセス ID。|  
  
|定義済みの SP ストアの種類|説明|  
|-------------------------------|-----------------|  
|storetypeFile|シンボルは、別のファイルに格納されます。|  
|storetypeMetadata|シンボルは、アセンブリ内にメタデータとして格納されます。|  
  
|その他のプロパティ|説明|  
|------------------------------|-----------------|  
|metricShowNonUserCode|設定 0 以外に、非ユーザー コードを表示します。|  
|metricJustMyCodeStepping|これに設定をステップ実行がユーザー コードでのみ発生することがあるかを示す 0 以外の値。|  
|metricCLSID|特定のメトリック型のオブジェクトの CLSID。|  
|MetricName|特定のメトリック型のオブジェクトのユーザー フレンドリ名。|  
|metricLanguage|言語の名前です。|  
  
## <a name="registry-locations"></a>レジストリの場所  
 メトリックの読み込みおよびで具体的には、レジストリに書き込まれる、`VisualStudio`サブキー。  
  
> [!NOTE]
>  ほとんどの場合、メトリックが HKEY_LOCAL_MACHINE キーに書き込まれます。 ただし、場合もあります HKEY_CURRENT_USER キーとなる、変換先です。 Dbgmetric.lib は、両方のキーを処理します。 HKEY_CURRENT_USER 検索メトリックを取得するときに最初に、次に HKEY_LOCAL_MACHINE です。 メトリックの設定には、パラメーターは使用するどの最上位のキーを指定します。  
  
 *[レジストリ キー]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[バージョン ルート]*\  
  
 *[メトリックのルート]*\  
  
 *[メトリックの種類]*\  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[レジストリ キー]*|`HKEY_CURRENT_USER` または `HKEY_LOCAL_MACHINE`。|  
|*[バージョン ルート]*|Visual Studio のバージョン (たとえば、 `7.0`、 `7.1`、または`8.0`)。 ただし、このルートを変更することもを使用して、 **/rootsuffix**に切り替える**devenv.exe**です。 VSIP、この修飾子は、通常**Exp**バージョン ルートである場合はたとえば、8.0Exp のため、します。|  
|*[メトリックのルート]*|これは、いずれかの`AD7Metrics`または`AD7Metrics(Debug)`dbgmetric.lib のデバッグ バージョンを使用するかどうかに応じて、します。 **注:**デバッグとリリースの違いがある場合、この名前付け規則に従う必要があります dbgmetric.lib を使用すると、かどうかのバージョンをレジストリに反映する必要があります。|  
|*[メトリックの種類]*|書き込まれるメトリックの種類: `Engine`、 `ExpressionEvaluator`、 `SymbolProvider`, などです。これらすべてとして dbgmetric.h のように定義されます`metricTypeXXXX`ここで、`XXXX`特定の種類の名前を指定します。|  
|*[metric]*|メトリックを設定するために値を割り当てるためのエントリの名前。 メトリックの実際の組織は、メトリックの種類によって異なります。|  
|*[メトリックの値]*|メトリックに割り当てられた値。 値は、(文字列、数値など) を持つ必要があります型は、メトリックによって異なります。|  
  
> [!NOTE]
>  すべての Guid の形式で格納`{GUID}`です。 たとえば、`{123D150B-FA18-461C-B218-45B3E4589F9B}` のようにします。  
  
### <a name="debug-engines"></a>デバッグ エンジン  
 レジストリのデバッグ エンジンのメトリックの構成を次に示します。 `Engine`デバッグ エンジンのメトリックの種類の名前に対応する*[メトリックの種類]*上記のレジストリ サブツリーでします。  
  
 `Engine`\  
  
 *[エンジン guid]*\  
  
 `CLSID` = *[クラス guid]*  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
 `PortSupplier`\  
  
 `0` = *[ポートのサプライヤーの guid]*  
  
 `1` = *[ポートのサプライヤーの guid]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[エンジン guid]*|デバッグ エンジンの GUID です。|  
|*[クラス guid]*|このデバッグ エンジンを実装するクラスの GUID です。|  
|*[ポートのサプライヤーの guid]*|存在する場合、ポート サプライヤーの GUID です。 多くのデバッグ エンジンは、既定ポート業者を使用し、独自の仕入先を指定しません。 この場合、サブキー`PortSupplier`は出力されません。|  
  
### <a name="port-suppliers"></a>ポートの仕入先  
 レジストリで、ポート供給業者のメトリックの組織を次に示します。 `PortSupplier`ポートのサプライヤーのメトリックの種類の名前に対応する*[メトリックの種類]*です。  
  
 `PortSupplier`\  
  
 *[ポートのサプライヤーの guid]*\  
  
 `CLSID` = *[クラス guid]*  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[ポートのサプライヤーの guid]*|ポートのサプライヤーの GUID|  
|*[クラス guid]*|このポート業者を実装するクラスの GUID|  
  
### <a name="symbol-providers"></a>プロバイダーのシンボル  
 レジストリでシンボル供給業者のメトリックの構成を次に示します。 `SymbolProvider`シンボルのプロバイダーのメトリックの種類の名前に対応する*[メトリックの種類]*です。  
  
 `SymbolProvider`\  
  
 *[シンボル プロバイダー guid]*\  
  
 `file`\  
  
 `CLSID` = *[クラス guid]*  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
 `metadata`\  
  
 `CLSID` = *[クラス guid]*  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[シンボル プロバイダー guid]*|シンボルのプロバイダーの GUID|  
|*[クラス guid]*|このシンボル プロバイダーを実装するクラスの GUID|  
  
### <a name="expression-evaluators"></a>式エバリュエーター  
 レジストリで、式エバリュエーターのメトリックの組織を次に示します。 `ExpressionEvaluator`式エバリュエーターのメトリックの種類の名前に対応する*[メトリックの種類]*です。  
  
> [!NOTE]
>  指標の種類の`ExpressionEvaluator`式エバリュエーターのメトリックの変更がすべてが適切な式エバリュエーターのメトリック関数を介して送られることが前提として、dbgmetric.h で定義されていない (のレイアウト、`ExpressionEvaluator`サブキーがある程度複雑になり、dbgmetric.lib 内部に詳細が隠されたように) します。  
  
 `ExpressionEvaluator`\  
  
 *[言語の guid]*\  
  
 *[ベンダー guid]*\  
  
 `CLSID` = *[クラス guid]*  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
 `Engine`\  
  
 `0` = *[デバッグ エンジン guid]*  
  
 `1` = *[デバッグ エンジン guid]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[言語の guid]*|言語の GUID|  
|*[ベンダー guid]*|仕入先の GUID|  
|*[クラス guid]*|この式エバリュエーターを実装するクラスの GUID|  
|*[デバッグ エンジン guid]*|この式エバリュエーターで動作するデバッグ エンジンの GUID|  
  
### <a name="expression-evaluator-extensions"></a>式エバリュエーターの拡張機能  
 式エバリュエーター拡張子メトリックは、レジストリ内の組織を次に示します。 `EEExtensions`指標の種類名、式エバリュエーターの拡張機能ありに対応しています*[メトリックの種類]*です。  
  
 `EEExtensions`\  
  
 *[拡張機能の guid]*\  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[拡張機能の guid]*|式エバリュエーターの拡張機能の GUID|  
  
### <a name="exceptions"></a>例外  
 レジストリの例外のメトリックの構成を次に示します。 `Exception`例外のメトリックの種類の名前に対応する*[メトリックの種類]*です。  
  
 `Exception`\  
  
 *[デバッグ エンジン guid]*\  
  
 *[例外の種類]*\  
  
 *[例外]*\  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
 *[例外]*\  
  
 *[metric] = [メトリックの値]*  
  
 *[metric] = [メトリックの値]*  
  
|プレースホルダー|説明|  
|-----------------|-----------------|  
|*[デバッグ エンジン guid]*|例外をサポートするデバッグ エンジンの GUID です。|  
|*[例外の種類]*|処理できる例外のクラスを識別するサブキーの一般的なタイトルです。 一般的な名前は**C++ 例外**、 **Win32 例外**、 **Common Language Runtime Exceptions**、および**ネイティブ ランタイム チェック**です。 これらの名前は、ユーザーには例外の特定のクラスにも使われます。|  
|*[例外]*|例外の名前。 たとえば、 **_com_error**または**コントロール ブレーク**です。 これらの名前は、ユーザーに特定の例外を識別するも使われます。|  
  
## <a name="requirements"></a>必要条件  
 これらのファイルにある、 [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK のインストール ディレクトリ (既定では、 *[ドライブ]*\Program Files\Microsoft Visual Studio 2010 SDK\\)。  
  
 ヘッダー: includes\dbgmetric.h  
  
 ライブラリ: libs\ad2de.lib、libs\dbgmetric.lib  
  
## <a name="see-also"></a>参照  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)