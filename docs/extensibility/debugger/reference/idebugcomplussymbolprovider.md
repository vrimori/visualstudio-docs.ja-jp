---
title: IDebugComPlusSymbolProvider |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 707cf44f6c4bff961df4225d23d8918ed4548e04
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948988"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
マネージ コードに固有のメソッドで COM + シンボル プロバイダーを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーター (EE) に利用できるインターフェイスとデバッグ エンジン (DE) で使用されることを意図したものに区別はありませんが、次のメソッドは DE 開発者だけをおそらく有用です。AreSymbolsLoaded、GetAddressesInModuleFromPosition、GetEntryPoint、GetFunctionLineOffset、GetLocalVariableLayout、IsFunctionStale、LoadSymbols、LoadSymbolsFromStream、ReplaceSymbols、UnloadSymbols、および UpdateSymbols します。  
  
## <a name="methods"></a>メソッド  
 メソッドだけでなく、 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)インターフェイスでは、このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|アプリケーション ドメイン id が指定された指定したモジュールのデバッグ シンボルが読み込まれるかどうかを決定します。|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|指定したプリミティブ型から型を作成します。|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|デバッグ アドレスの配列を指定したモジュールのドキュメントの位置をマップします。|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|については、デバッグ アドレスが指定されて、指定した配列の型を取得します。|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|そのモジュールとアプリケーション ドメインが指定されたアセンブリの名前を取得します。|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|指定されたプログラミング言語で実装されている指定した属性クラスを取得します。|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|指定されたモジュールで指定された属性を持つクラスを取得します。|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|アプリケーションのエントリ ポイントを取得します。|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|指定した行オフセットを表す関数内でアドレスを取得します。|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|一連のメソッドのローカル変数のレイアウトを取得します。|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|特定のメタデータ オブジェクトの指定したトークンに関連付けられた名前を返します。|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|指定したモジュールの指定した親属性で、デバッグ シンボルを取得します。|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|アンマネージ コードで使用されるシンボル リーダーを取得します。|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|そのデバッグ アドレスを指定された記号の型を取得します。|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|指定されたデバッグ アドレスで関数が削除されたかどうかを決定します。|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|かどうか、指定されたデバッグ アドレスに、この関数は古いと見なさを決定します。|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|かどうか、デバッガーを指定したアドレスにあるコードが非表示を決定します。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|メモリ内の指定されたデバッグ シンボルを読み込みます。|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|読み込みでは、データ ストリームを指定するシンボルをデバッグします。|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|指定したデータ ストリームの現在のデバッグ シンボルを置き換えます。|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|メモリから指定したモジュールのデバッグ シンボルをアンロードします。|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|指定したデータ ストリームとメモリのデバッグ シンボルを更新します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー:Sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll