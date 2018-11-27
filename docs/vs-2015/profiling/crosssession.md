---
title: CrossSession | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d0282ec76bb3907cca4e2b08be9f036c3d38400b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803566"
---
# <a name="crosssession"></a>CrossSession
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **CrossSession** オプションを使用すると、プロファイラーはあらゆるコンソール セッションからデータを収集できます。 **CrossSession** オプションは、**Start** オプションと共に使用する必要があります。  
  
 **CrossSession** の代わりに省略形の **CS** を利用できます。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし  
  
## <a name="valid-options"></a>有効なオプション  
 別のセッションでプロファイリングを有効にするには、**CrossSession** オプションは **Start** オプションと共に指定する必要があります。 **CrossSession** は、後続の **VSPerfCmd Attach** コマンドと **Detach** コマンドでも指定する必要があります。  
  
 **Start:** `Method`  
 **Start** オプションは、指定したプロファイル方法にプロファイラーを初期化します。  
  
 **Attach:** _PID_[**,**_PID_]  
 指定されたプロセスのプロファイリングを開始します。  
  
 **Detach**[**:**_PID_[,_PID_]]  
 指定されたプロセスのプロファイリングを停止します。  
  
## <a name="example"></a>例  
 この例では、別のコンソール セッションで開始されたアプリケーションにアタッチするために **CrossSession** オプションが使用されます。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)



