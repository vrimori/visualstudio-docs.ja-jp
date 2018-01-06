---
title: "IDebugPortPicker::DisplayPortPicker |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1f3dc923bc9a835581439b6de9307de452f24801
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
ユーザーがポートを選択できる指定されたダイアログ ボックスが表示されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [in]親ダイアログ ボックスのハンドルです。  
  
 `pbstrPortId`  
 [out]ポートの識別子の文字列です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 戻り値の`S_FALSE`(または戻り値の`S_OK`で、 `BSTR` 'éý' `NULL`)、ユーザーがクリックされたことを示します**キャンセル**です。  
  
## <a name="see-also"></a>参照  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)