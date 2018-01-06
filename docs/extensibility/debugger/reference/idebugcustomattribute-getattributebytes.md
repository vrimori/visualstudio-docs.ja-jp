---
title: "IDebugCustomAttribute::GetAttributeBytes |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords: IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4cde5d8f27c7961e3b9ed7bda34473d755226072
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
バイトの blob として属性情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppBlob`  
 [入力、出力].属性データが入力配列。  
  
 `pdwLen`  
 [入力、出力].返されるバイトの最大数を指定します、`ppBlob`配列を配列に実際に書き込まれたバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 設定、`ppBlob`属性使用できるバイト数のパラメーターに null 値の数を取得します。 配列を割り当てて、しのでは、その配列を渡す、`ppBlob`パラメーター。  
  
 属性のバイトは、カスタム属性の生データを表します。  
  
## <a name="see-also"></a>参照  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)