---
title: "デバッグ用の SDK ヘルパー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dbgmetric.lib"
  - "レジストリ、SDK のデバッグ"
  - "SDK では、レジストリの場所のデバッグ"
  - "dbgmetric.h"
  - "メトリック [SDK のデバッグ]"
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# デバッグ用の SDK ヘルパー
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

これらの関数と宣言はC\+\+ のデバッグ エンジン式エバリュエーターとシンボルのプロバイダーを実装するためのグローバルなヘルパー関数です。  
  
> [!NOTE]
>  これらの関数と宣言のマネージ バージョンは現時点ではありません。  
  
## 概要  
 デバッグ エンジン式エバリュエーターと Visual Studio を使用したシンボルのプロバイダーには登録する必要があります。  これはレジストリのキーとそのエントリを設定して構成しますが「メトリックとして以外の場合はと呼ばれます」。次のグローバル関数がこれらの測度を更新するプロセスを簡単にするために設計されています。  これらの関数によって更新される各レジストリ キーの項目のレイアウトを確認するためにレジストリの場所のセクションを参照してください。  
  
## 概要メトリック関数  
 これらはデバッグ エンジンで使用される一般的な関数です。  式エバリュエーターとシンボルのプロバイダー用に特化された関数は後で詳しく説明します。  
  
### GetMetric のメソッド  
 レジストリからメトリック値を取得します。  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|パラメーター|Description|  
|------------|-----------------|  
|pszMachine|\[入力\] 登録を書き込むリモート コンピューターの名前 \(`NULL` ローカル コンピューターを意味します。|  
|pszType|\[入力\] メトリックスの種類の 1 つが。|  
|guidSection|\[入力\] 特定のエンジンエバリュエーター例外などの GUID   これは特定の要素にメトリックスの種類の下のサブセクションを指定します。|  
|pszMetric|\[入力\] 取得される測度。  これは特定の値の名前に対応します。|  
|pdwValue|\[入力\] メトリックスの値の格納場所。  ダブル ワード型 \(この例に示すようにGUID の BSTRGUIDまたは配列を返すことができます GetMetric の複数の特徴があります。|  
|pszAltRoot|\[入力\] 使用される代替のレジストリ ルート。  既定値を使用する場合 `NULL` に設定します。|  
  
### SetMetric のメソッド  
 レジストリ指定のメトリック値を設定します。  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|パラメーター|Description|  
|------------|-----------------|  
|pszType|\[入力\] メトリックスの種類の 1 つが。|  
|guidSection|\[入力\] 特定のエンジンエバリュエーター例外などの GUID   これは特定の要素にメトリックスの種類の下のサブセクションを指定します。|  
|pszMetric|\[入力\] 取得される測度。  これは特定の値の名前に対応します。|  
|dwValue|\[入力\] メトリックスの値の格納場所。  ダブル ワード型 \(この例ではGUID\) の BSTRGUIDまたは配列を格納できる SetMetric の複数の特徴があります。|  
|fUserSpecific|\[入力\] メトリックをユーザー別およびローカル コンピューター ハイブではなくユーザー書き込まれたらハイブに変更します。|  
|pszAltRoot|\[入力\] 使用される代替のレジストリ ルート。  既定値を使用する場合 `NULL` に設定します。|  
  
### RemoveMetric のメソッド  
 レジストリから指定したメトリックを削除します。  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|パラメーター|Description|  
|------------|-----------------|  
|pszType|\[入力\] メトリックスの種類の 1 つが。|  
|guidSection|\[入力\] 特定のエンジンエバリュエーター例外などの GUID   これは特定の要素にメトリックスの種類の下のサブセクションを指定します。|  
|pszMetric|\[入力\] 削除される測度。  これは特定の値の名前に対応します。|  
|pszAltRoot|\[入力\] 使用される代替のレジストリ ルート。  既定値を使用する場合 `NULL` に設定します。|  
  
### EnumMetricSections のメソッド  
 レジストリのさまざまなメトリック セクションを列挙します。  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|パラメーター|Description|  
|------------|-----------------|  
|pszMachine|\[入力\] 登録を書き込むリモート コンピューターの名前 \(`NULL` ローカル コンピューターを意味します。|  
|pszType|\[入力\] メトリックスの種類の 1 つが。|  
|rgguidSections|\[入力出力\] 入力する GUID の割り当て済みの配列。|  
|pdwSize|\[入力\] `rgguidSections` の配列に格納できる GUID の最大数。|  
|pszAltRoot|\[入力\] 使用される代替のレジストリ ルート。  既定値を使用する場合 `NULL` に設定します。|  
  
## 式エバリュエーターの関数  
  
|Function|Description|  
|--------------|-----------------|  
|GetEEMetric|レジストリからメトリック値を取得します。|  
|SetEEMetric|レジストリ指定のメトリック値を設定します。|  
|RemoveEEMetric|レジストリから指定したメトリックを削除します。|  
|GetEEMetricFile|ファイル名を指定しから派生し読み込みファイルの内容を文字列として返します。|  
  
## 例外関数  
  
|Function|Description|  
|--------------|-----------------|  
|GetExceptionMetric|レジストリからメトリック値を取得します。|  
|SetExceptionMetric|レジストリ指定のメトリック値を設定します。|  
|RemoveExceptionMetric|レジストリから指定したメトリックを削除します。|  
|RemoveAllExceptionMetrics|レジストリからすべての例外のメトリックを削除します。|  
  
## シンボルのプロバイダーの関数  
  
|Function|Description|  
|--------------|-----------------|  
|GetSPMetric|レジストリからメトリック値を取得します。|  
|SetSPMetric|レジストリ指定のメトリック値を設定します。|  
|RemoveSPMetric|レジストリから指定したメトリックを削除します。|  
  
## 列挙関数  
  
|Function|Description|  
|--------------|-----------------|  
|EnumMetricSections|指定のメトリックのすべてのメトリックを列挙します。|  
|EnumDebugEngine|登録されたデバッグ エンジンを列挙します。|  
|EnumEEs|登録された式エバリュエーターを列挙します。|  
|EnumExceptionMetrics|すべての例外のメトリックを列挙します。|  
  
## 非常定義  
 これらの定義は定義済みのメトリック名前を使用できます。  ワイド文字列で定義された名前が対応するすべてさまざまなレジストリ キーとレジストリ値の名前です : たとえば`extern LPCWSTR metrictypeEngine`。  
  
|定義済みのメトリックの種類|例 : 基本キーのです。|  
|-------------------|------------------|  
|metrictypeEngine|すべてのエンジンのメトリックをデバッグします。|  
|metrictypePortSupplier|すべてがサプライヤーのメトリックを移植します。|  
|metrictypeException|すべての例外の測度。|  
|metricttypeEEExtension|すべての式エバリュエーターを拡張。|  
  
|エンジンのプロパティのデバッグ|Description|  
|---------------------|-----------------|  
|metricAddressBP|アドレス ブレークポイントのサポートを示す\) 以外に設定します。|  
|metricAlwaysLoadLocal|以外に設定デバッグ エンジンを常にローカルに読み込む場合は。|  
|metricLoadInDebuggeeSession|使用しない|  
|metricLoadedByDebuggee|デバッグ エンジンはデバッグ対象プログラムとして常に読み込まれたことを示すためにゼロ以外に設定します。|  
|metricAttach|既存のプログラムに添付ファイルをサポートする場合はに設定します。|  
|metricCallStackBP|呼び出し履歴のブレークポイントのサポートを示す\) 以外に設定します。|  
|metricConditionalBP|条件付きブレークポイントの設定をサポートする場合はに設定します。|  
|metricDataBP|データの変更のブレークポイントの設定をサポートする場合はに設定します。|  
|metricDisassembly|逆アセンブリの一覧を開発する場合をサポートする場合はに設定します。|  
|metricDumpWriting|ダンプの記述 \(出力デバイスに対するメモリ ダンプ\) のサポートを示す\) 以外に設定します。|  
|metricENC|編集のサポートを示す場合はそれ以外に設定します。 **Note:**  カスタムのデバッグ エンジンでは設定しないでくださいしを 0 にして常に設定する必要があります。|  
|metricExceptions|例外のサポートを示す\) 以外に設定します。|  
|metricFunctionBP|名前付きブレークポイント \(のサポートを特定の関数名が呼び出されたときに中断ブレークポイント示す\) 以外に設定します。|  
|metricHitCountBP|「ヒット」 \(位置のブレークポイントの設定のサポートが発生した後のみ設定されたブレークポイントにヒットすると時間\) する場合はに設定します。|  
|metricJITDebug|例外は実行中のプロセスに発生する場合\) Just\-In\-Time デバッグのサポートを表示する以外に設定します。デバッガーが起動します。|  
|metricMemory|使用しない|  
|metricPortSupplier|1 つが実行されるポートのサプライヤーの CLSID を設定します。|  
|metricRegisters|使用しない|  
|metricSetNextStatement|\(ゼロ以外に設定するをサポートする中間ステートメントの実行を省略\) 次のステートメントを指定します。|  
|metricSuspendThread|スレッドの実行を中断できます。をサポートする場合はに設定します。|  
|metricWarnIfNoSymbols|シンボルがない場合はユーザーに通知する必要があることを示すためにゼロ以外に設定します。|  
|metricProgramProvider|プログラムのプロバイダーの CLSID を設定します。|  
|metricAlwaysLoadProgramProviderLocal|プログラムのプロバイダーが常にローカルにあることを示すためにゼロ以外に設定します。|  
|metricEngineCanWatchProcess|デバッグ エンジンはプログラムのプロバイダーではなくプロセス イベントを監視できます。を表示する以外に設定します。|  
|metricRemoteDebugging|リモート デバッグのサポートを表示する以外に設定します。|  
|metricEncUseNativeBuilder|示すためにを以外の値に設定を編集しアプリケーションをデバッグ エンジンの encbuild.dll を編集する場合は次の行で使用する必要があります。 **Note:**  カスタムのデバッグ エンジンでは設定しないでくださいしを 0 にして常に設定する必要があります。|  
|metricLoadUnderWOW64|64 ビット プロセスをデバッグするときにデバッグ エンジンが WOW のデバッグ対象プロセスに読み込まれることを示すためにゼロ以外に設定します。; はデバッグ エンジン \(WOW64 で実行されているの Visual Studio プロセス読み込まれます。|  
|metricLoadProgramProviderUnderWOW64|WOW の下の 64 ビット プロセスをデバッグするとプログラムのプロバイダーがデバッグ対象のプロセスで読み込まれることを示すためにゼロ以外に設定します。; それ以外の場合はVisual Studio プロセスに読み込まれます。|  
|metricStopOnExceptionCrossingManagedBoundary|ハンドルされない例外がマネージ コードとアンマネージ コードの境界を越えてスローされるプロセスが停止する必要があることを示すためにゼロ以外に設定します。|  
|metricAutoSelectPriority|デバッグ エンジンの自動選択の優先順位を設定します \(の値は優先順位に等しい場合\)。|  
|metricAutoSelectIncompatibleList|自動選択を無視するデバッグ エンジンに対して GUID を指定するエントリを含むレジストリ キー。  これらのエントリは文字列として表現される GUID の最初の \(012 など\) です。|  
|metricIncompatibleList|このデバッグ エンジンに対応しないデバッグ エンジンに対して GUID を指定するエントリを含むレジストリ キー。|  
|metricDisableJITOptimization|最適化が Just\-In\-Time デバッグ時に \(マネージ コードの場合\) に無効にする必要があることを示すためにゼロ以外に設定します。|  
  
|式エバリュエーターのプロパティ|Description|  
|---------------------|-----------------|  
|metricEngine|これは指定されたの式エバリュエーターをサポートするデバッグ エンジンの値が保持されます。|  
|metricPreloadModules|式エバリュエーターはプログラムに対して起動時にモジュールが事前に積まれる必要があることを示すためにゼロ以外に設定します。|  
|metricThisObjectName|このオブジェクト名 「」に設定します。|  
  
|式エバリュエーターを拡張プロパティ|Description|  
|-----------------------|-----------------|  
|metricExtensionDll|この拡張機能をサポートするにはdll の名前。|  
|metricExtensionRegistersSupported|サポートされているレジスタの一覧。|  
|metricExtensionRegistersEntryPoint|登録にアクセスするためのエントリ ポイント。|  
|metricExtensionTypesSupported|サポートされる型のリスト。|  
|metricExtensionTypesEntryPoint|型にアクセスするためのエントリ ポイント。|  
  
|サプライヤーのプロパティを移植します。|Description|  
|-------------------------|-----------------|  
|metricPortPickerCLSID|ポートの指定 \(ポートをクリックしてデバッグに使用するポートを追加するためにユーザーが使用できる CLSID\) ダイアログ ボックスが表示されます。|  
|metricDisallowUserEnteredPorts|ユーザーが入力したポートがサプライヤーのポート \(追加できない場合はこれ以外はポート ピッカー ダイアログ ボックスで主に読み取り専用にします\)。|  
|metricPidBase|プロセス ID を割り当てるときのサプライヤーのポートで使用される基本のプロセス ID。|  
  
|定義済みの SP ストアの種類|Description|  
|---------------------|-----------------|  
|storetypeFile|シンボルが別のファイルに格納されます。|  
|storetypeMetadata|シンボルはアセンブリ内にメタデータとして格納されます。|  
  
|そのほかのプロパティ|Description|  
|----------------|-----------------|  
|metricShowNonUserCode|非使用者コードを表示する以外に設定します。|  
|metricJustMyCodeStepping|手順ではユーザー コードでのみ実行できることを示すためにゼロ以外に設定します。|  
|metricCLSID|特定のメトリックの種類のオブジェクトの CLSID。|  
|metricName|特定のメトリックの種類のオブジェクトのわかりやすい名前。|  
|metricLanguage|言語名。|  
  
## レジストリの場所  
 メトリックスはから読み込まれ`VisualStudio` のサブ キーのレジストリに書き込まれます \(特に。  
  
> [!NOTE]
>  ほとんどの場合メトリックスは HKEY\_LOCAL\_MACHINE キーに書き込まれます。  ただしHKEY\_CURRENT\_USER は対象のキーです。  Dbgmetric.lib は両方のキーを処理します。  メトリックを取得するとHKEY\_CURRENT\_USER とHKEY\_LOCAL\_MACHINE 最初に検索します。  これはメトリックを設定する場合パラメーターを使用すると最上位レベルのキーを指定します。  
  
 *\[入力\] レジストリ キー* \\  
  
 `Software`\\  
  
 `Microsoft`\\  
  
 `VisualStudio`\\  
  
 *\[出力\] バージョンのルート* \\  
  
 *\[ルート メトリック\]*\\  
  
 *\[入力出力\]*\\  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
|プレースホルダー|Description|  
|--------------|-----------------|  
|*\[入力\] レジストリ キー*|`HKEY_CURRENT_USER` または `HKEY_LOCAL_MACHINE`。|  
|*\[出力\] バージョンのルート*|Visual Studio のバージョン \(`7.0``7.1`または `8.0`\)。  ただしこのルートは**devenv.exe** への **\/rootsuffix** スイッチを使用して変更できます。  VSIP ではこの修飾子はExp. であるためバージョンのルートは8.0Exp です。|  
|*\[ルート メトリック\]*|これは dbgmetric.lib のデバッグ バージョンを使用するかどうかを `AD7Metrics` または `AD7Metrics(Debug)`です。 **Note:**  dbgmetric.lib が使用されたかこの名前付け規則はレジストリに反映するリリース バージョンとデバッグの違いが従う必要があります。|  
|*\[入力出力\]*|書き込むメトリックスの型 : `Engine``ExpressionEvaluator``SymbolProvider` など\)   これらはすべてが特定の種類の名前と dbgmetric.h のように定義されます。|  
|*\[メトリック\]*|値を割り当てるエントリの名前を設定します。  メトリックスの実際の整理やメトリックスの種類によって異なります。|  
|*\[メトリック値\]*|メトリックスに割り当てられた値。  値がで \(文字列数値など\) で必要な型が決まります。|  
  
> [!NOTE]
>  すべての GUID は `{GUID}` の形式で格納されます。  たとえば、`{123D150B-FA18-461C-B218-45B3E4589F9B}` のようにします。  
  
### デバッグ エンジン  
 次はレジストリのデバッグ エンジンの測度の構成です。  `Engine` はデバッグ エンジン メトリック型名で最上位のレジストリのサブ ツリーの *\[入力出力\]* に対応します。  
  
 `Engine`\\  
  
 *\[エンジン guid\]*\\  
  
 `CLSID` \= *\[クラス guid\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 `PortSupplier`\\  
  
 `0` \= *\[ポートのサプライヤー guid\]*  
  
 `1` \= *\[ポートのサプライヤー guid\]*  
  
|プレースホルダー|Description|  
|--------------|-----------------|  
|*\[エンジン guid\]*|デバッグ エンジンの GUID。|  
|*\[クラス guid\]*|このデバッグ エンジンを実装するクラスの GUID。|  
|*\[ポートのサプライヤー guid\]*|ポートのサプライヤーの GUID です \(存在する場合\)。  多くのデバッグ エンジンは既定のポートの業者を使用して独自の業者を指定しません。  この場合そのキー `PortSupplier` は属性です。|  
  
### ポートのサプライヤー  
 次はレジストリのポートのサプライヤーのメトリックの構成です。  `PortSupplier` はポートのサプライヤー メトリック型名で*\[入力出力\]* に対応します。  
  
 `PortSupplier`\\  
  
 *\[ポートのサプライヤー guid\]*\\  
  
 `CLSID` \= *\[クラス guid\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
|プレースホルダー|Description|  
|--------------|-----------------|  
|*\[ポートのサプライヤー guid\]*|ポートのサプライヤーの GUID|  
|*\[クラス guid\]*|このポートの業者を実装するクラスの GUID|  
  
### シンボルのプロバイダー  
 次はレジストリのシンボルがサプライヤーのメトリックの構成です。  `SymbolProvider` はシンボルのメトリック プロバイダーの型名で*\[入力出力\]* に対応します。  
  
 `SymbolProvider`\\  
  
 *\[シンボルのプロバイダーの GUID 入力\]*\\  
  
 `file`\\  
  
 `CLSID` \= *\[クラス guid\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 `metadata`\\  
  
 `CLSID` \= *\[クラス guid\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
|プレースホルダー|Description|  
|--------------|-----------------|  
|*\[シンボルのプロバイダーの GUID 入力\]*|シンボルのプロバイダーの GUID|  
|*\[クラス guid\]*|このシンボルのプロバイダーを実装するクラスの GUID|  
  
### 式エバリュエーター  
 次はレジストリの式エバリュエーターの測度の構成です。  `ExpressionEvaluator` は式エバリュエーター メトリック型名で*\[入力出力\]* に対応します。  
  
> [!NOTE]
>  `ExpressionEvaluator` のメトリックの種類は dbgmetric.h の式エバリュエーターのすべての変更は非常に適切な式エバリュエーター メトリック関数によって進むことが想定されるため定義されていません \(`ExpressionEvaluator` のサブ キーのレイアウトは若干複雑です。つまり詳細は dbgmetric.lib 内で非表示になります\)。  
  
 `ExpressionEvaluator`\\  
  
 *\[言語 guid\]*\\  
  
 *\[販売元 guid\]*\\  
  
 `CLSID` \= *\[クラス guid\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 `Engine`\\  
  
 `0` \= *\[デバッグ エンジン guid\]*  
  
 `1` \= *\[デバッグ エンジン guid\]*  
  
|プレースホルダー|Description|  
|--------------|-----------------|  
|*\[言語 guid\]*|言語の GUID|  
|*\[販売元 guid\]*|販売元の GUID|  
|*\[クラス guid\]*|この式エバリュエーターを実装するクラスの GUID|  
|*\[デバッグ エンジン guid\]*|この式エバリュエーターを使用してデバッグ エンジンの GUID|  
  
### 式エバリュエーターの拡張子  
 次はレジストリの式エバリュエーターを拡張したメトリックの構成です。  `EEExtensions` は式エバリュエーターを拡張したメトリック型名で*\[入力出力\]* に対応します。  
  
 `EEExtensions`\\  
  
 *\[拡張子 guid\]*\\  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
|プレースホルダー|Description|  
|--------------|-----------------|  
|*\[拡張子 guid\]*|式エバリュエーターを拡張子の GUID|  
  
### 例外  
 次はレジストリの例外の測度の構成です。  `Exception` は例外のメトリック型名で*\[入力出力\]* に対応します。  
  
 `Exception`\\  
  
 *\[デバッグ エンジン guid\]*\\  
  
 *\[入力\] 例外の種類* \\  
  
 *\[例外\]*\\  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[例外\]*\\  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
 *\[メトリック\] \= \[メトリック値\]*  
  
|プレースホルダー|Description|  
|--------------|-----------------|  
|*\[デバッグ エンジン guid\]*|そのデバッグ エンジンの GUID は例外をサポートします。|  
|*\[入力\] 例外の種類*|処理できる例外のクラスを識別するキーの概要のタイトル。  一般的な名前 **C\+\+ Exceptions** は**Win32 ExceptionsCommon Language Runtime Exceptions** と **Native Run\-Time Checks** です。  これらの名前がユーザーに固有の例外クラスを識別するために使用されます。|  
|*\[例外\]*|例外名 : たとえば**\_com\_error** または **Control\-Break**。  これらの名前がユーザーに特定の例外を識別するために使用されます。|  
  
## 要件  
 これらのファイルは [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK のインストール ディレクトリ \(既定では *ドライブ \[入力\]*\\ Program Files \\ Microsoft Visual Studio 2010 SDK \\\) にあります。  
  
 ヘッダー : INCLUDE \\ dbgmetric.h  
  
 ライブラリ : Lib \\ \\ ad2de.lib ライブラリ dbgmetric.lib  
  
## 参照  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)