---
title: Idiastackwalkframe::searchforreturnaddress |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddress method
ms.assetid: 1a54c50d-94af-4a43-ac4e-d80c5df156c3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef962774f9af45e705d9e3b6111056b0da23d405
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731914"
---
# <a name="idiastackwalkframesearchforreturnaddress"></a>IDiaStackWalkFrame::searchForReturnAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

最も近い関数のリターン アドレスの指定したスタック フレームを検索します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT searchForReturnAddress (   
   IDiaFrameData* frame,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `frame`  
 [in][IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)現在のスタック フレームを表すオブジェクト。  
  
 `returnAddress`  
 [out]最も近い関数のリターン アドレスを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



