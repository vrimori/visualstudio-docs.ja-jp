---
title: "IDebugCustomViewer::DisplayValue |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 74990eac497b8ed239894121eb954cd8eeca55e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
このメソッドは、指定された値を表示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `hwnd`  
 [in]親ウィンドウ  
  
 `dwID`  
 [in]複数の種類をサポートしているカスタム ビューアーの ID。  
  
 `pHostServices`  
 [in]予約されています。 常に設定を null にします。  
  
 `pDebugProperty`  
 [in]表示される値を取得するために使用するインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`; エラー コードを返しますそれ以外の場合。  
  
## <a name="remarks"></a>コメント  
 表示は、このメソッドは、必要なウィンドウを作成、値を表示、入力には、待機し、ウィンドウを閉じて、呼び出し元に戻す前にすべて「モーダル」です。 つまり、メソッドは、ウィンドウを破棄するためのユーザー入力を待機しているため、出力のウィンドウの作成から、プロパティの値を表示するすべての側面を処理する必要があります。  
  
 値の変更をサポートするために、指定された[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)オブジェクトを使用する、 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)メソッド — 場合は、値を文字列として表現できます。 以外の場合は、カスタム インターフェイスを作成するために必要な — これを実装する、式エバリュエーターに限定`DisplayValue`メソッド — を実装する、同じオブジェクトに対して、`IDebugProperty3`インターフェイスです。 このカスタム インターフェイスを任意のサイズや複雑さのデータを変更する方法を指定します。  
  
## <a name="see-also"></a>参照  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)