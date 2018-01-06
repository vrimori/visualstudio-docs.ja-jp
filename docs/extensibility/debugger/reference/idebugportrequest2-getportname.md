---
title: "IDebugPortRequest2::GetPortName |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortRequest2::GetPortName
helpviewer_keywords: IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5906560574836390656254055130af3275fa4f76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
ポートの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrPortName`  
 [out]ポートの名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)が通常に渡されたインターフェイス デバッグ パッケージ (クライアント) から、接続を取得するポート業者 (サーバー) にポートです。 デバッグ パッケージと、ポート供給業者の両方には、ポートの選択肢の認識します。 単純な文字列は、ポートを記述できる場合、`IDebugPortRequest2::GetPortName`メソッドには、接続を作成するための十分な情報です。 それ以外の場合、追加のインターフェイスは、サーバーを使用して取得できるクライアントによって提供されること`IDebugPortRequest2::QueryInterface`です。  
  
## <a name="see-also"></a>参照  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)