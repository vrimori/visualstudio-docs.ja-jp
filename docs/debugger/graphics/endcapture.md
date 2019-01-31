---
title: EndCapture |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8f72e3bcd3755fe59af5207586cf9cf03d432f4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967626"
---
# <a name="endcapture"></a>EndCapture
`BeginCapture` で開始されたキャプチャ区間を終了します。  
  
## <a name="syntax"></a>構文  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>コメント  
 特定種類の描画呼び出しに関するグラフィック情報だけをキャプチャするときなど、キャプチャ区間は通常 1 つのフレームのサブセットに及びます。 キャプチャ区間が present への呼び出しに及ぶ場合は、2 つのフレームのグラフィックス情報がキャプチャされます。 最初のフレームは、`BeginCapture` への呼び出しと present への呼び出しの間の区間に及びます。2 つ目のフレームは、present への呼び出しの後の最初の Direct3D イベントと `EndCapture` への呼び出しの間の区間に及びます。  
  
 間隔をキャプチャするには、キャプチャしてグラフィックス情報を記録するアプリを準備する必要があります: 呼び出したする必要があります、 [Init](init.md)のインスタンスを通じて、`VsgDbg`クラスを呼び出す前に`BeginCapture`または`EndCapture`します。  
  
## <a name="see-also"></a>「  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)