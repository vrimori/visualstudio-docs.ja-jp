---
title: '方法: Web アプリケーションのデバッグ |Microsoft Docs'
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
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e185b1b35a2462547ca8689dc1a4bfe80ff036
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260813"
---
# <a name="how-to-debug-web-applications"></a>方法: Web アプリケーションをデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web アプリケーションの開発の主要なテクノロジは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] デバッガーには、ローカルまたはリモート サーバーで [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web アプリケーションをデバッグするための強力なツールが用意されています。 このトピックでは、デバッグする方法を説明します、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]開発中のプロジェクト。 デバッグする方法については、 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web アプリケーションを実稼働サーバーに配置されているを参照してください[デプロイされた Web アプリケーションのデバッグ](../debugger/debugging-deployed-web-applications.md)します。  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] アプリケーションをデバッグするには  
  
-   適切なアクセス許可が必要です。 詳細については、「 [System Requirements](../debugger/aspnet-debugging-system-requirements.md)」をご覧ください。  
  
-   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 有効にする必要がありますデバッグ**プロジェクト プロパティ**します。  
  
-   アプリケーションの構成ファイル (Web.config) をデバッグ モードに設定する必要があります。 デバッグ モードの [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] では、動的に生成されたファイル用のシンボルが生成され、デバッガーの [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] アプリケーションへのアタッチが可能になります。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] では、プロジェクトを Web プロジェクト テンプレートから作成した場合は、デバッグ開始時にこの処理が自動的に実行されます。  
  
-   詳細については、次を参照してください。[方法: ASP.NET アプリケーションのデバッグを有効にする](../debugger/how-to-enable-debugging-for-aspnet-applications.md)します。  
  
### <a name="to-debug-a-web-application-during-development"></a>開発時に Web アプリケーションをデバッグするには  
  
1.  **デバッグ** メニューのをクリックして**開始**Web アプリケーションのデバッグを開始します。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] では、Web アプリケーション プロジェクトのビルド、必要に応じたアプリケーションの配置、ローカルでデバッグしている場合に ASP.NET 開発サーバーの起動、および [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスへのアタッチを実行します。  
  
2.  デバッガーを使用して、ほかのアプリケーションの場合と同様に、ブレークポイントの設定と解除、ステップの実行、およびその他のデバッグ処理を行います。  
  
     詳細については、次を参照してください。[デバッガーの基本事項](../debugger/debugger-basics.md)します。  
  
3.  **デバッグ** メニューのをクリックして**デバッグの停止** 、デバッグ セッションを終了または上、**ファイル**Internet Explorer で、メニューのをクリックして**閉じる**します。  
  
## <a name="see-also"></a>関連項目  
 [Web アプリケーションとスクリプトのデバッグ](../debugger/debugging-web-applications-and-script.md)   
 [ASP.NET および AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [方法:ASP.NET アプリケーションのデバッグを有効にする](../debugger/how-to-enable-debugging-for-aspnet-applications.md)



