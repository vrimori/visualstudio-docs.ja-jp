---
title: 'エラー: asp.NET がインストールされていない |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0617f5200a69809afc86fe9405dc3ea9bd8fcda0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540268"
---
# <a name="error-aspnet-not-installed"></a>エラー ： ASP .NET がインストールされていません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: ASP.NET がインストールされていない](https://docs.microsoft.com/visualstudio/debugger/error-aspnet-not-installed)します。  
  
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



