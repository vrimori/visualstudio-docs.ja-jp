---
title: "IDebugCustomAttributeQuery2::GetCustomAttributeByName |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 4d3b06a21b70934863403289fc549815ed515883
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
カスタム属性の名前で指定されたカスタム属性のバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszCustomAttributeName`  
 [in]検索するカスタム属性の名前を含む文字列。  
  
 `ppBlob`  
 [入力、出力].カスタム属性データが入力配列。  
  
 `pdwLen`  
 [入力、出力].返されるバイトの最大数を指定します、`ppBlob`配列を配列に実際に書き込まれたバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。 または、カスタム属性が存在しない場合は S_FALSE を返します。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 設定、`ppBlob`属性使用できるバイト数のパラメーターに null 値の数を取得します。 配列を割り当てて、しのでは、その配列を渡す、`ppBlob`パラメーター。  
  
 属性のバイトは、カスタム属性の生データを表します。  
  
 場合、`ppBlob`と`pdwLen`パラメーターに null 値に設定されて、このメソッドは、カスタム属性の単なる存在確認に使用できます。 簡単に代わりに、ただしが呼び出されて、 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
