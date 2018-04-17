---
title: 'エラー: asp.NET がインストールされていない |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 41d2804ce3cab18acf697333ee9950b4717f9500
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="error-aspnet-not-installed"></a>エラー ： ASP .NET がインストールされていません。
このエラーは、デバッグを実行しようとしているコンピューターに [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] が正しくインストールされていない場合に発生します。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] がインストールされていないか、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] がインストールされてから IIS がインストールされた可能性があります。  
  
### <a name="to-reinstall-aspnet"></a>ASP.NET を再インストールするには  
  
1.  コマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     ここで*バージョン*v1.0.370 など、コンピューターにインストールされている .NET Framework のバージョン番号を表します。 によって、framework のバージョンを確認することができます、`\WINDOWS\Microsoft.NET\Framework`ディレクトリ。  
  
    > [!NOTE]
    >  Windows Server 2003 にインストールできます[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]を使用して**プログラム追加と削除**コントロール パネルの します。  
  
## <a name="see-also"></a>関連項目  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)