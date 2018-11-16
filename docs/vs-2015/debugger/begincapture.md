---
title: BeginCapture |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d9ac50f2e1f5f92a16a7482a25c9054c2a36f68
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787310"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`EndCapture` で終了するキャプチャ区間を開始します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Remarks  
 特定種類の描画呼び出しに関するグラフィック情報だけをキャプチャするときなど、キャプチャ区間は通常 1 つのフレームのサブセットに及びます。 キャプチャ区間が present への呼び出しに及ぶ場合は、2 つのフレームのグラフィックス情報がキャプチャされます。 最初のフレームは、`BeginCapture` への呼び出しと present への呼び出しの間の区間に及びます。2 つ目のフレームは、present への呼び出しの後の最初の Direct3D イベントと `EndCapture` への呼び出しの間の区間に及びます。  
  
 間隔をキャプチャするには、キャプチャしてグラフィックス情報を記録するアプリを準備する必要があります: 呼び出したする必要があります、 [Init](../debugger/init.md)のインスタンスを通じて、`VsgDbg`クラスを呼び出す前に`BeginCapture`または`EndCapture`します。  
  
## <a name="see-also"></a>関連項目  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)



