---
title: IDebugObject::GetValue |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c43487960fdca21e4c716514a3533db90c6ae76
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770268"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

連続した一連のバイトとしてオブジェクトの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pValue`  
 [入力、出力]入力が連続する一連のオブジェクトの値を表すバイト配列。  
  
 `nSize`  
 [in]フェッチするバイトの最大数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 呼び出すことでフェッチできる値のバイトの合計数を取得、 [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

