---
title: Output | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bca95dea2ac381d28d2c2a4043f94dcfb6fd6e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922264"
---
# <a name="output"></a>出力
**Output** オプションでは、パフォーマンス セッションのプロファイル データ ファイルの名前を指定します。 **Output** は **Start** オプションと共に使用する必要があります。  
  
## <a name="syntax"></a>構文  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [サービスのプロファイリング](../profiling/command-line-profiling-of-services.md)