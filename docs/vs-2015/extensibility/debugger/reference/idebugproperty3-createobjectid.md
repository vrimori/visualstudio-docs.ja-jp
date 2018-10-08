---
title: IDebugProperty3::CreateObjectID |Microsoft Docs
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
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5b7ca39a36bafe2ebba838c7f6d03f89e2f8132
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538651"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProperty3::CreateObjectID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-createobjectid)します。  
  
その他のすべてのプロパティ間で一意であることを確認するこのプロパティの一意の ID を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 セッション デバッグ マネージャーがこのプロパティは、その他のすべてのプロパティの間で一意に識別することを確認するときに、このメソッドが呼び出されます。 デバッグ エンジン (DE) は、処理プロパティが既に一意に識別される場合を除き、このメソッドをサポートしています。 返すかどうか、DE は、このメソッドをサポートしていません、`E_NOTIMPL`します。  
  
 一意の ID が作成された`CreateObjectID`が破棄されるときに、 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)メソッドが呼び出される; も、このプロパティを一意に識別するための必要性の終端を表すこれです。  
  
> [!NOTE]
>  一意の Id にして必要な DE を行うことができます、この一意の ID を取得するメソッドがないときに、`CreateObjectID`メソッドが呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)

