---
title: 'エラー: asp.NET がインストールされていない |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20a6d85fbdc7fad9077a19704b6c448c73dae787
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739589"
---
# <a name="error-aspnet-not-installed"></a>エラー ： ASP .NET がインストールされていません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このエラーは、デバッグを実行しようとしているコンピューターに [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] が正しくインストールされていない場合に発生します。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] がインストールされていないか、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] がインストールされてから IIS がインストールされた可能性があります。  
  
### <a name="to-reinstall-aspnet"></a>ASP.NET を再インストールするには  
  
1.  コマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     場所*バージョン*v1.0.370 など、コンピューターにインストールされている .NET Framework のバージョン番号を表します。 によってフレームワークのバージョンを確認することができます、`\WINDOWS\Microsoft.NET\Framework`ディレクトリ。  
  
    > [!NOTE]
    >  Windows Server 2003 では、インストールすることができます[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]を使用して**プログラム追加と削除**コントロール パネルの します。  
  
## <a name="see-also"></a>関連項目  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



