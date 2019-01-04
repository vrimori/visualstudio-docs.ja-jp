---
title: IDebugPortRequest2::GetPortName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c916e379c5a5f3f50fbad8d6b38548f2b0603eff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940136"
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
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)が通常に渡されたインターフェイス デバッグ パッケージ (クライアント) からポートのサプライヤー (サーバー) の接続を取得するポート。 パッケージのデバッグとポートのサプライヤーの両方は、ポートに対して多数の選択肢に注意してください。 単純な文字列は、ポートを記述できる場合、`IDebugPortRequest2::GetPortName`メソッドには、接続を作成するのに十分な情報。 サーバーを使用して取得できるクライアントによって追加のインターフェイスを指定する場合は、`IDebugPortRequest2::QueryInterface`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)