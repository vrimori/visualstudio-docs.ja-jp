---
title: VSG_NODEFAULT_INSTANCE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 675bd0ceef2b8eef382891bf0fc4b42400ca9df4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018658"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
既定のインスタンスかどうかをその存在によって定義、 [VsgDbg クラス](vsgdbg-class.md)クラス: プログラムによるキャプチャ インターフェイスを提供する — が指定されています。  
  
## <a name="syntax"></a>構文  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>[値]  
 その有無によって `VsgDbg` クラスの既定のインスタンスが提供されるかどうかを判断するプリプロセッサ シンボル。 このシンボルが定義されている場合は、`VsgDbg` クラスの既定のインスタンスは提供されません。それ以外の場合は、プログラムの実行前に既定のインスタンスが提供され、初期化されます。  
  
 プログラムによるキャプチャ インターフェイスは、グローバル スコープを持つポインター `g_pVsgDbg` を通じて提供されます。  
  
```cpp
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>コメント  
 ほとんどの場合は既定のインスタンスで十分ですが、D3D デバイスが DLL の外部で作成されたときのその DLL 内部のプログラムによるキャプチャ インターフェイスを使用するには、`VsgDbg` クラスの独自のインスタンスを作成および管理する必要があります。 プログラムによるキャプチャの API への独自のインターフェイスをこのように管理している場合は、オーバーヘッドを避けるために、`VSG_NODEFAULT_INSTANCE` を定義して既定のインスタンスを無効にします。  
  
 既定のインスタンスが無効になっていない場合は、プログラムの実行前に自動的に初期化され、プログラムの終了時に自動的に破棄されます。 このインスタンスの初期化および初期化解除を明示的に行う必要はありません。  
  
 定義する必要があります、既定のインスタンスを無効にする`VSG_NODEFAULT_INSTANCE`インクルードする前に`vsgcapture.h`プログラムでします。  
  
## <a name="example"></a>例  
 次の例は、既定のインスタンスを無効にする方法を示しています。  
  
```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```
