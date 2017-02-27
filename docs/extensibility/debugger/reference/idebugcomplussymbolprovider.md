---
title: "IDebugComPlusSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider インターフェイス"
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

マネージ コードに固有のメソッドと COM\+ プロバイダーのシンボルを表します。  
  
## 構文  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## 実装についてのメモ  
 式エバリュエーターに役立つと \(EE\) デバッグ エンジン \(DE\) によって使用されるように設計されたインターフェイスインターフェイス間に分離が次のメソッドはde\-DE developers だけに必要な : AreSymbolsLoadedGetAddressesInModuleFromPositionGetEntryPointGetFunctionLineOffsetGetLocalVariableLayoutIsFunctionStaleLoadSymbolsLoadSymbolsFromStreamReplaceSymbolsUnloadSymbols と UpdateSymbols。  
  
## メソッド  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[AreSymbolsLoaded](../Topic/IDebugComPlusSymbolProvider::AreSymbolsLoaded.md)|デバッグ シンボルがアプリケーション ドメインの識別子が指定したモジュールに読み込むかどうかを判定します。|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|プリミティブ型指定の型を作成します。|  
|[GetAddressesInModuleFromPosition](../Topic/IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition.md)|デバッグのアドレスの配列に指定したモジュール内のドキュメント内の位置をマップします。|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|デバッグのアドレスを指定された配列に関する情報を取得する型。|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|モジュールおよびアプリケーション ドメインを含むアセンブリの名前を取得します。|  
|[GetAttributedClassesForLanguage](../Topic/IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage.md)|特定のプログラミング言語で実装される指定された属性クラスを取得します。|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|指定したモジュール内の指定した属性クラスを取得します。|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|アプリケーションのエントリ ポイントを取得します。|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|特定の行のオフセットを表す関数内のアドレスを取得します。|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|一連のメソッドのローカル変数のレイアウトを取得します。|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|メタデータ オブジェクトに対して指定したトークンに関連付けられた名前を返します。|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|指定したモジュールの特定の親の属性のデバッグ シンボルを取得します。|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|アンマネージ コードで使用するシンボル リーダーを取得します。|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|デバッグのアドレスを持つシンボルの型のを取得します。|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|デバッグ指定の関数のアドレスを削除するかどうかを判定します。|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|デバッグ指定の関数のアドレスが古い見なされるかどうかを判定します。|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|デバッガーのアドレス指定のコードが非表示かどうかを判断します。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|メモリの指定はデバッグ シンボルを読み込みます。|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|データ ストリームはデバッグ シンボルを読み込みます。|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|指定されたデータ ストリームの要素と現在のデバッグ シンボルを置き換えます。|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|指定したメモリの指定したモジュールのデバッグ シンボルをアンロードします。|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|これらのメモリのデバッグ シンボルで指定したデータ ストリームを更新します。|  
  
## 必要条件  
 ヘッダー : Sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll