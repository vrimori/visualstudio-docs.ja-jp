---
title: "IDebugEngine3::SetSymbolPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetSymbolPath"
helpviewer_keywords: 
  - "IDebugEngine3::SetSymbolPath"
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ シンボルが検索パスを設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```c#  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### パラメーター  
  
|パラメーター|Description|  
|------------|-----------------|  
|`szSymbolSearchPath`|\[入力\] 文字列のシンボル検索パス。  詳細については「解説」を参照してください。  null にすることはできません。|  
|`szSymbolCachePath`|\[入力\] 文字列シンボルをキャッシュできるローカル パス。  null にすることはできません。|  
|`Flags`|\[入力\] 使われません ; 常に 0 に設定します。|  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コードを返します。  
  
## 解説  
 文字列 `szSymbolSearchPath` はシンボルを検索するにはセミコロンで区切られた一つ以上のパスのリストです。  これらのパスにはスタイルのローカル パスUNC パスURL のいずれでもかまいません。  これらのパスにはさまざまな種類のミックスを指定できます。  は UNC パス \(\\ \\ \\ Symserver シンボル\) の場合デバッグ エンジンはパスがシンボル サーバーにありそのサーバーからシンボルを読み込めるするかどうかを調べ指定したパスで `szSymbolCachePath` してキャッシュします。  
  
 シンボル パスは一つ以上のキャッシュの場所を含めることができます。  キャッシュは優先順位のキャッシュの優先順位と\*および区切り記号に示します。  次に例を示します。  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) のメソッドはシンボルの実際の読み込みを実行します。  
  
## 参照  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)