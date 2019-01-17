---
title: IProvideExpressionContexts::EnumExpressionContexts |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dd18408235a5621354531a2fd228ff44a19d6a1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088713"
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
このコンポーネントによって認識されている式コンテキストの列挙子を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppedec`  
 [out]このコンポーネントによって認識されている式コンテキストの列挙子。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 プロセス デバッグ マネージャーでは、このメソッドを使用して、特定のスレッドに関連付けられているすべてのグローバル式のコンテキストを検索します。  
  
> [!NOTE]
>  このメソッドは、関心のあるスレッド内からを呼び出されます。 現在のスレッドを識別して適切な列挙子を返すために、実装者の責任です。  
  
## <a name="see-also"></a>関連項目  
 [IProvideExpressionContexts インターフェイス](../../winscript/reference/iprovideexpressioncontexts-interface.md)