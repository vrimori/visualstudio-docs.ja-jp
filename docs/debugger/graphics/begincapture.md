---
title: "BeginCapture |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e1c7c0f57b919271c4880c9c1f2fbd8ca1dc964f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [EndCapture](endcapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)