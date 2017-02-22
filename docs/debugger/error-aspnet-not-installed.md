---
title: "エラー ： ASP .NET がインストールされていません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http_not_supported"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, インストールのエラー メッセージ"
  - "デバッガー, Web アプリケーション エラー"
  - "エラー メッセージ, ASP.NET"
  - "Web アプリケーション, エラー"
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー ： ASP .NET がインストールされていません。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このエラーは、デバッグを実行しようとしているコンピューターに [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] が正しくインストールされていない場合に発生します。  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] がインストールされていないか、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] がインストールされてから IIS がインストールされた可能性があります。  
  
### ASP.NET を再インストールするには  
  
1.  コマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     *version* は、コンピューターにインストールされている .NET Framework のバージョン番号です \(v1.0.370 など\)。  .Net Framework のバージョンは、`\WINDOWS\Microsoft.NET\Framework` ディレクトリで確認できます。  
  
    > [!NOTE]
    >  Windows Server 2003 の場合は、コントロール パネルの **\[アプリケーションの追加と削除\]** を使って [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] をインストールできます。  
  
## 参照  
 [Web アプリケーションのデバッグ : エラーおよびトラブルシューティング](../debugger/debugging-web-applications-errors-and-troubleshooting.md)