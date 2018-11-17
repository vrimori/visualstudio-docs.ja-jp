---
title: 'デバッグの準備: ASP.NET Web アプリケーション |Microsoft Docs'
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
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 59f4f3e1db92c5f7b46a9bb9e1e164fc25b01010
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730689"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>デバッグの準備 : ASP.NET Web アプリケーション
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Web サイト テンプレートは、Web フォーム アプリケーションを作成します。 このテンプレートを使用して Web サイトを作成する場合、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] はデバッグ用に既定の設定を作成します。 **プロジェクト プロパティ**ダイアログ ボックスで、Web ページをスタート ページにするかどうか指定できます。 デバッグを開始すると、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]これらの既定の設定を使用した Web サイト[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Internet Explorer を起動し、デバッガーをアタッチします、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]ワーカー プロセス (aspnet_wp.exe または w3wp.exe)。 詳細については、「 [System Requirements](../debugger/aspnet-debugging-system-requirements.md)」をご覧ください。  
  
### <a name="to-create-a-web-forms-application"></a>Web フォーム アプリケーションを作成するには  
  
1.  **ファイル**] メニューの [選択**新しい Web サイト**します。  
  
2.  **新しい Web サイト**ダイアログ ボックスで、 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **Web サイト**します。  
  
3.  **[OK]** をクリックします。  
  
### <a name="to-debug-your-web-form"></a>Web フォームをデバッグするには  
  
1.  関数とイベント ハンドラーに 1 つ以上のブレークポイントを設定します。  
  
     詳細については、「 [Breakpoints and Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)」を参照してください。  
  
2.  ブレークポイントに達したら、関数内のコードをステップ実行します。 問題が特定されるまでコードの実行を確認します。  
  
     詳細については、次を参照してください。[ステッピング](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9)と[Web アプリケーションのデバッグとスクリプト](../debugger/debugging-web-applications-and-script.md)します。  
  
## <a name="changing-default-configurations"></a>既定の構成の変更  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で作成された既定のデバッグ構成とリリース構成を変更する必要がある場合は、構成を変更できます。 詳細については、「[方法: デバッグ構成とリリース構成を設定する](../debugger/how-to-set-debug-and-release-configurations.md)」を参照してください。  
  
#### <a name="to-change-the-default-debug-configuration"></a>既定のデバッグ構成を変更するには  
  
1.  **ソリューション エクスプ ローラー**を Web サイトを右クリックし、**プロパティ ページ**を開く、**プロパティ ページ** ダイアログ ボックス。  
  
2.  クリックして**開始オプション**します。  
  
3.  設定**開始動作**最初に表示される Web ページにします。  
  
4.  **デバッガー**、ことを確認します**ASP.NET デバッグ**が選択されています。  
  
     詳細については、次を参照してください。 [Web プロジェクトのプロパティ ページ設定](../debugger/property-pages-settings-for-web-projects.md)します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)



