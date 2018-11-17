---
title: TargetCLR | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 517cf1eccd296716b0105539f6ae81cbc3519fd0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759302"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**TargetCLR** オプションでは、アプリケーションに複数のバージョンの CLR (共通言語ランタイム) が読み込まれている場合に、プロファイリングを行う CLR のバージョンを指定します。  
  
 既定では、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイル ツールはアプリケーションによって読み込まれる最初の CLR のバージョンを対象とします。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>パラメーター  
 `ClrVersion`  
 CLR のバージョン番号。 **vN.N.NNNNN** のバージョン形式を使用します。  
  
## <a name="required-options"></a>必須オプション  
 **TargetCLR** オプションは、**Launch** オプションまたは **Attach** オプションと共に指定する場合にのみ使用できます。  
  
 **Launch:** `AppName`  
 指定したアプリケーションを起動し、プロファイリングを開始します。  
  
 **Attach:** `PID`  
 指定したプロセスのプロファイリングを開始します。  
  
## <a name="example"></a>例  
 この例では、TargetCLR オプションを使用して、CLR バージョン 4.0.11003 がプロファイリングされることを確認します。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```



