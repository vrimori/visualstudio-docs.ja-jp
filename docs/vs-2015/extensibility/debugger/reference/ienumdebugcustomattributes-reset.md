---
title: IEnumDebugCustomAttributes::Reset |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4faa2fb3b2286f014e3ab0dc40cb3c94469faaf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537434"
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IEnumDebugCustomAttributes::Reset](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugcustomattributes-reset)します。  
  
列挙のシーケンスを最初にリセットします。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが呼び出された後、次回の呼び出し、[次](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)メソッドが列挙体の最初の要素を返します。  
  
## <a name="see-also"></a>関連項目  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [次へ](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)

