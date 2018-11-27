---
title: IDebugProcess3::DisableENC |Microsoft Docs
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
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d518ce42642e683fa5f38f67ce9f8458f9a0979
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807115"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドに明示的に無効にします。 エディット コンティニュでこのプロセス (およびすべてのプログラムが含まれています)。 カスタム ポート サプライヤーが常に返す必要があります`E_NOTIMPL`します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `reason`  
 [in]値、 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)列挙体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  カスタム ポート サプライヤーが常に返す必要があります`E_NOTIMPL`します。  
  
## <a name="remarks"></a>Remarks  
 1 回の編集しプロセスの続行は無効です、プロセスを再起動することによってのみ再度有効にできます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

