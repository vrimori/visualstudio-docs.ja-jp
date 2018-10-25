---
title: IDebugPortRequest2::GetPortName |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 490381f183a19e33fd391b133562fc2a463c6ee9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920847"
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