---
title: IDebugEngine3::SetSymbolPath |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5a79cfd817be1a665f0008a39420e7cb39cc50b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115487"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
パスまたはデバッグ シンボルの検索パスを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in]シンボル検索パスまたはパスを含む文字列です。 詳細については、「解説」を参照してください。 null にすることはできません。|  
|`szSymbolCachePath`|[in]シンボルをキャッシュできるローカル パスを含む文字列です。 null にすることはできません。|  
|`Flags`|[in]使用されません。常に 0 に設定します。|  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 文字列`szSymbolSearchPath`シンボルを検索、セミコロンで区切られた 1 つまたは複数のパスの一覧を示します。 これらのパスは、ローカル パス、UNC 形式のパスまたは URL にすることができます。 これらのパスには、さまざまな種類のミックスことができます。 パスが UNC である場合 (たとえば、 \\\Symserver\Symbols)、デバッグ エンジンは、パスがシンボル サーバーがあり、それらによって指定されたパスでのキャッシュ、そのサーバーからシンボルを読み込むことができるようかどうかかを確認する必要がありますして`szSymbolCachePath`です。  
  
 シンボル パスは、1 つ以上のキャッシュの場所を含めることもできます。 キャッシュが最初に、キャッシュとの最も高い優先度の優先度順に表示されで区切られた * 記号。 例えば:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)メソッドは、シンボルの実際の負荷を実行します。  
  
## <a name="see-also"></a>関連項目  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)