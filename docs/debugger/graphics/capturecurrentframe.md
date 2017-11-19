---
title: "CaptureCurrentFrame |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcdeee28077f2c7affd1c4cd1f82d8c8cb29494b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
現在のフレームの残りの部分を、グラフィックス ログ ファイルにキャプチャします。  
  
## <a name="syntax"></a>構文  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>コメント  
 `BeginCapture` 関数によって開始されたキャプチャなど、別のキャプチャ操作が進行中の場合、そのキャプチャ操作は完了し、別個のフレームとしてグラフィックス ログに記録されます。 その直後、グラフィック診断によって現在のフレームの残りの部分のキャプチャが開始され、それも個別のフレームとして記録されます。 present への呼び出しによって、現在のフレームの末尾がマークされます。  
  
 フレームをキャプチャするには、キャプチャしてグラフィックス情報を記録するアプリを準備する必要があります: つまり、する必要がありますが呼び出さ[Init](init.md)のインスタンスを通じて、`VsgDbg`クラスを呼び出す前に`CaptureCurrentFrame`です。  
  
## <a name="see-also"></a>関連項目  
 [Init](init.md)   
 [BeginCapture](begincapture.md)