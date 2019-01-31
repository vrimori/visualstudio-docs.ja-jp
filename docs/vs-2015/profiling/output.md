---
title: Output | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26a9532bcf0e641d9ad27522f207493b905dc471
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776958"
---
# <a name="output"></a>出力
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Output** オプションでは、パフォーマンス セッションのプロファイル データ ファイルの名前を指定します。 **Output** は **Start** オプションと共に使用する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `FileName`  
 データ ファイルの名前。 完全パスまたは部分パスで指定できます。 パスが指定されていない場合、ファイルは現在のディレクトリに作成されます。  
  
## <a name="required-options"></a>必須オプション  
 **Output** オプションは、**Start** オプションと共に使用する必要があります。  
  
 **Start:** `Method`  
 出力ファイル名を指定します。  
  
## <a name="example"></a>例  
 次の例では、現在のディレクトリにプロファイル データ ファイルが作成されます。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>「  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)
