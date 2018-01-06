---
title: "VSG_NODEFAULT_INSTANCE |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7f94aa50908097b161929e51f260d3bcc058bd5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
既定のインスタンスかどうかをその存在によって定義、 [VsgDbg クラス](vsgdbg-class.md)クラス: プログラムによるキャプチャ インターフェイスを提供する — を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>[値]  
 その有無によって `VsgDbg` クラスの既定のインスタンスが提供されるかどうかを判断するプリプロセッサ シンボル。 このシンボルが定義されている場合は、`VsgDbg` クラスの既定のインスタンスは提供されません。それ以外の場合は、プログラムの実行前に既定のインスタンスが提供され、初期化されます。  
  
 プログラムによるキャプチャ インターフェイスは、グローバル スコープを持つポインター `g_pVsgDbg` を通じて提供されます。  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>コメント  
 ほとんどの場合は既定のインスタンスで十分ですが、D3D デバイスが DLL の外部で作成されたときのその DLL 内部のプログラムによるキャプチャ インターフェイスを使用するには、`VsgDbg` クラスの独自のインスタンスを作成および管理する必要があります。 プログラムによるキャプチャの API への独自のインターフェイスをこのように管理している場合は、オーバーヘッドを避けるために、`VSG_NODEFAULT_INSTANCE` を定義して既定のインスタンスを無効にします。  
  
 既定のインスタンスが無効になっていない場合は、プログラムの実行前に自動的に初期化され、プログラムの終了時に自動的に破棄されます。 このインスタンスの初期化および初期化解除を明示的に行う必要はありません。  
  
 既定のインスタンスを無効にする必要がありますを定義する`VSG_NODEFAULT_INSTANCE`インクルードする前に`vsgcapture.h`プログラムでします。  
  
## <a name="example"></a>例  
 次の例は、既定のインスタンスを無効にする方法を示しています。  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```