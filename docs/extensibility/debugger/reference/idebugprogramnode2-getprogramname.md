---
title: "IDebugProgramNode2::GetProgramName |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: cc3772fd6808542e36a464e4ea1c0a460e6c882d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
プログラムの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetProgramName (   
   BSTR* pbstrProgramName  
);  
```  
  
```csharp  
int GetProgramName (   
   out string pbstrProgramName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrProgramName`  
 [out]プログラムの名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 プログラムの名は、プログラムの名前がそのようなパスの一部にすることがありますが、プログラムへのパスと同じ動作ではありません。  
  
## <a name="example"></a>例  
 次の例は、単純なは、このメソッドを実装する方法を示します`CProgram`を実装するオブジェクト、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)インターフェイスです。 `MakeBstr`関数が BSTR として指定した文字列のコピーを割り当てます。  
  
```cpp  
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {    
   if (!pbstrProgramName)    
      return E_INVALIDARG;    
  
   // Assign the member program name to the passed program name.    
   *pbstrProgramName = MakeBstr(m_pszProgramName);    
   return NOERROR;    
}    
```  
  
## <a name="see-also"></a>参照  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)