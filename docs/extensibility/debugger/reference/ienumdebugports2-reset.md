---
title: "IEnumDebugPorts2::Reset |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPorts2::Reset
helpviewer_keywords: IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fdcf2fbe5349b4f404a8b1d8ad71f754a759230f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Reset
最初の要素に列挙体をリセットします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドが呼び出された後、次の呼び出し、[次](../../../extensibility/debugger/reference/ienumdebugports2-next.md)メソッドが列挙体の最初の要素を返します。  
  
## <a name="see-also"></a>参照  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)