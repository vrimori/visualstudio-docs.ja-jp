---
title: IApplicationDebugger::CreateInstanceAtDebugger |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6495c2d8782d1128700bdfb6d4081b80ffae878
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725772"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
コードによってデバッガー プロセス内のオブジェクトの作成を許可されているアウトのプロセスをデバッガーにします。  
  
> [!IMPORTANT]
>  これにより、信頼されたデバッガー スレッドで任意のオブジェクトを作成するコードを信頼されていないため、このメソッドを実装いない必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `rclsid`  
 [in]クラスの id (CLSID) を作成するオブジェクト。  
  
 `pUnkOuter`  
 [in]場合`NULL`集計の一部として、オブジェクトが作成されていません。 それ以外の場合、`pUnkOuter`集約オブジェクトへのポインターは、`IUnknown`インターフェイス (制御`IUnknown`)。  
  
 `dwClsContext`  
 [in]実行可能コードの実行コンテキスト。 値が列挙体から取得されます`CLSCTX`です。  
  
 `riid`  
 [in]オブジェクトとの通信に使用されるインターフェイスの識別子です。  
  
 `ppvObject`  
 [out]要求されたインターフェイス ポインターを受け取るポインター変数のアドレス`riid`です。 成功時に、*`ppvObject`要求されたインターフェイス ポインターを格納します。 障害時に、 \* `ppvObject`含む`NULL`です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドからデリゲートを`CoCreateInstance`です。  
  
 メソッドは現在実装されていません。  
  
## <a name="see-also"></a>関連項目  
 [IApplicationDebugger インターフェイス](../../winscript/reference/iapplicationdebugger-interface.md)