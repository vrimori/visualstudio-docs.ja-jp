---
title: IDebugEngine3::SetSymbolPath |Microsoft Docs
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
ms.openlocfilehash: 00f493c0c64dc8bc6bef6adff59fff4ce1bcb8c3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854573"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
デバッグ シンボルを検索するパスを設定します。  
  
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
|`szSymbolSearchPath`|[in]シンボルの検索パスまたはパスを含む文字列。 詳細については、「解説」を参照してください。 null にすることはできません。|  
|`szSymbolCachePath`|[in]シンボルをキャッシュできるローカル パスを含む文字列。 null にすることはできません。|  
|`Flags`|[in]使用されません。常に 0 に設定します。|  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 文字列`szSymbolSearchPath`シンボルの検索には、セミコロンで区切られた 1 つまたは複数のパスの一覧を示します。 これらのパスは、ローカル パス、UNC 形式のパスまたは URL にあることができます。 これらのパスには、さまざまな種類の混在こともできます。 パスが UNC である場合 (たとえば、 \\\Symserver\Symbols)、デバッグ エンジンは、パスがシンボル サーバーがあり、によって指定されたパスでキャッシュして、そのサーバーからシンボルを読み込むことができるようかどうかかを確認する必要がありますして`szSymbolCachePath`します。  
  
 シンボル パスは、1 つまたは複数のキャッシュの場所を含めることもできます。 キャッシュが最初に、最高の優先順位のキャッシュを使用して、優先順位の順序で一覧を表示してで区切られた * 記号。 例えば:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)メソッドは、シンボルの実際の負荷を実行します。  
  
## <a name="see-also"></a>関連項目  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)