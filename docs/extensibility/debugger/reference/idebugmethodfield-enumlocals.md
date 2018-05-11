---
title: IDebugMethodField::EnumLocals |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8379407a275fa4b89b4107037b2a39691d062dd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
メソッドの選択したローカル変数の列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAddress`  
 [in][IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)コンテキストまたはローカル変数の取得元のスコープを選択するデバッグ アドレスを表すオブジェクト。  
  
 `ppLocals`  
 [out]返します、 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)ローカル変数の一覧を表すオブジェクト。 それ以外の場合、ローカル変数が存在しない場合、null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。 または、ローカル変数が存在しない場合は S_FALSE を返します。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 指定されたデバッグ アドレスを含むブロック内で定義されている変数のみが列挙されます。 すべてコンパイラによって生成されたローカル変数を含むすべてのローカル変数が必要な場合は、呼び出し、 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)メソッドです。  
  
 メソッドは、複数のスコープのコンテキストまたはブロックを含めることができます。 たとえば、次の不自然なメソッドには、3 つのスコープ、2 つの内部ブロックと、メソッド本体が含まれています。  
  
```csharp  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)オブジェクトが表す、`func`メソッド自体です。 呼び出す、`EnumLocals`メソッドを[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)に設定、`Inner Scope 1`アドレスを含む列挙を返します、`temp1`例については、変数です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)