---
title: BeginCapture |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a93eb940e848767412b87509ed5f9e8845afdb66
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="begincapture"></a>BeginCapture
`EndCapture` で終了するキャプチャ区間を開始します。  
  
## <a name="syntax"></a>構文  
  
```C++  
void BeginCapture();  
```  
  
## <a name="remarks"></a>コメント  
 特定種類の描画呼び出しに関するグラフィック情報だけをキャプチャするときなど、キャプチャ区間は通常 1 つのフレームのサブセットに及びます。 キャプチャ区間が present への呼び出しに及ぶ場合は、2 つのフレームのグラフィックス情報がキャプチャされます。 最初のフレームは、`BeginCapture` への呼び出しと present への呼び出しの間の区間に及びます。2 つ目のフレームは、present への呼び出しの後の最初の Direct3D イベントと `EndCapture` への呼び出しの間の区間に及びます。  
  
 間隔を取得するには、キャプチャしてグラフィックス情報を記録するアプリを準備する必要があります: つまり、する必要がありますが呼び出さ[Init](init.md)のインスタンスを通じて、`VsgDbg`クラスを呼び出す前に`BeginCapture`または`EndCapture`です。  
  
## <a name="see-also"></a>関連項目  
 [EndCapture](endcapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)