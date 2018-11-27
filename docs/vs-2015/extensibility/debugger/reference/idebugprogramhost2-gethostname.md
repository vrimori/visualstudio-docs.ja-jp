---
title: IDebugProgramHost2::GetHostName |Microsoft Docs
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
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d19901134de6cf33d0b15f6fe65cc379662ec58
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807471"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

タイトル、フレンドリ名、またはこのプログラムのホスト プロセスのファイル名を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwType`  
 [in]値、 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)列挙体。  
  
 `pbstrHostName`  
 [out]要求されたホスト プロセスの名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、の一般的な実装で、`dwType`パラメーターは無視され、ホスト コンピューターのフレンドリ名が返されます。 もう 1 つの考えられる実装は、`dwType`への呼び出しにパラメーター、 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)メソッド名を取得します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

