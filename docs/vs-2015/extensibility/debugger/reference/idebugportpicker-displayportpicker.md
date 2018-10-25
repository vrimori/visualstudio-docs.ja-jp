---
title: IDebugPortPicker::DisplayPortPicker |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73565bb0d191e3aa70c319c290972883df4f1d3f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814377"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ユーザーがポートを選択できる指定されたダイアログ ボックスが表示されます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `hwndParentDialog`  
 [in]親ダイアログ ボックスのハンドル。  
  
 `pbstrPortId`  
 [out]ポート id 文字列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 戻り値`S_FALSE`(または戻り値の`S_OK`で、`BSTR`に設定`NULL`)、ユーザーがクリックされたことを示します**キャンセル**します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)

