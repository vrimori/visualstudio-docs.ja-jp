---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs
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
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0f3c8d43e0186ff368494d65a681ded58ef7f2bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765944"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

非推奨とされます。 使用しないでください。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrHostMachineName`  
 [out]プログラムが実行されているマシンの名前を返します。  
  
## <a name="return-value"></a>戻り値  
 実装は常に返す必要があります`E_NOTIMPL`します。  
  
## <a name="remarks"></a>Remarks  
  
> [!WARNING]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]、このメソッドは使用されなくと常に返す必要があります`E_NOTIMPL`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

