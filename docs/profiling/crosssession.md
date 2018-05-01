---
title: CrossSession | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ae3c401a08df3eefa6f2ebe247aa7404f6b4ed2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="crosssession"></a>CrossSession
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
  
 **Attach:** *PID*[**,***PID*]  
 指定されたプロセスのプロファイリングを開始します。  
  
 **Detach**[**:***PID*[,*PID*]]  
 指定されたプロセスのプロファイリングを停止します。  
  
## <a name="example"></a>例  
 この例では、別のコンソール セッションで開始されたアプリケーションにアタッチするために **CrossSession** オプションが使用されます。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>参照  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)