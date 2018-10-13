---
title: IDebugCustomAttributeQuery2 |Microsoft Docs
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
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d26f05172dc0ee4b5de2870a3ae24acc436684e8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276238"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このフィールドのカスタム属性の存在を定義し、存在する場合は、属性の情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーを実装する同一のオブジェクトにこのインターフェイスを実装する[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)カスタム属性をサポートするためにします。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 使用[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)からこのインターフェイスを取得する、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの**IDebugCustomAttributeQuery**インターフェイス。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|名前でカスタム属性が存在するかどうかを判断します。|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|指定されたカスタム属性の属性情報を取得します。|  
  
 加え、 **IDebugCustomAttributeQuery**メソッド、`IDebugCustomAttributeQuery2`次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|このフィールドにアタッチされているすべてのカスタム属性の列挙子を取得します。|  
  
## <a name="remarks"></a>Remarks  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)メソッドは、このフィールドに対して定義されているすべてのカスタム属性の列挙子を返すことができます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

