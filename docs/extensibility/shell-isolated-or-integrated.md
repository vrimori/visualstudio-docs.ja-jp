---
redirect_url: shell/shell-isolated-or-integrated
title: "Shell (Isolated または統合) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 787fd7c6980df9809fed9582f4ec8da81de8f862
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="shell-isolated-or-integrated"></a>Shell (Isolated または統合)
統合または分離モードで Visual Studio ベース アプリケーションを作成することができます。 統合モードでは、多くの Visual Studio 機能をアプリケーションだけでなく使用します。 分離のモードでは、独自の拡張と共に配布する Visual Studio の機能のサブセットを選択します。  
  
## <a name="integrated-mode"></a>統合モード  
 統合モードでは、ユーザーが標準の Visual Studio の機能とともに、カスタム ツールを使用します。 Integrated shell は、主にプログラミング言語とソフトウェア開発ツールをホストします。  
  
 Integrated shell で自動的に構築されたカスタム ツールは、同じコンピューターにインストールされている Visual Studio の他の任意のエディションとマージします。 Visual Studio が既にインストールされていない場合は、Visual Studio の統合シェルの再頒布可能パッケージ バージョンを指定できます。  
  
 Visual Studio の統合シェルの再頒布可能パッケージのバージョンでは、プログラミング言語と、それぞれのプロジェクト システムをサポートする機能は含まれません。  
  
> [!NOTE]
>  Visual Studio Express エディション以外のすべてのエディションと Visual Studio シェル統合モードをインストールすることができます。  
  
 詳細については、次を参照してください。 [Visual Studio Shell (Integrated)](../extensibility/visual-studio-shell-integrated.md)です。  
  
## <a name="isolated-mode"></a>分離モード  
 分離モードでは、サイド バイ サイドを実行するカスタム ツールを作成できます。 Visual Studio の他のバージョンとします。 目的が、主に標準の Visual Studio のすべての機能に応じてなしの Visual Studio サービスにアクセスできるツールです。 Visual Studio 分離シェルに基づいて構築されたアプリケーションの外観をカスタマイズすることができます。 簡単に、機能とメニュー コマンド グループ、アプリケーションと共に表示されるたくないをオフにすることができます。  
  
 詳細については、次を参照してください。 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)です。  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>統合または分離シェル アプリケーションを配布します。  
 統合または分離シェル アプリケーションを配布するためには、アプリケーションを特殊な統合または分離シェル再頒布可能パッケージ、およびインストール プログラムを含める必要があります。 配布とインストールの詳細については、次を参照してください。[分離シェル アプリケーションを配布する](../extensibility/distributing-isolated-shell-applications.md)です。  
  
> [!IMPORTANT]
>  [使用許諾契約書 (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552)シェルには Visual Studio と統合されており、特定のデータ コレクションに関するセクションが含まれています (**セクション 3 です。データ**)。  これには、顧客の使用状況データ、アプリケーションをビルドするか、内蔵または分離シェル ソフトウェアのユーザーから Microsoft によって収集される可能性がありますをについて説明します。 詳細については、次を参照してください。 [Microsoft Visual Studio の製品ファミリ プライバシーに関する声明](https://www.visualstudio.com/en-us/dn948229)です。  
>   
>  お客様からアプリケーションを別の使用状況データを収集する場合を収集するのアプリケーションのユーザーに適切な通知を提供する必要があります。  Visual Studio ソフトウェア開発キット ライセンスに従って、アプリケーションの一部として分離または統合シェル ソフトウェアを配布するときに、次のいずれかを含める必要があります。  
>   
>  -   アプリケーションのライセンスの一部として使用許諾契約書  
> -   統合セキュリティまたはシェル ソフトウェアの Microsoft のエンド ユーザー ライセンス条項と分離シェルが、最低でも、Visual Studio を保護する条項に同意するお客様を必要とする独自の EULA  
  
## <a name="additional-resources"></a>その他のリソース  
 再頒布可能パッケージの詳細については、次を参照してください。、 [Visual Studio 拡張機能のダウンロード](http://go.microsoft.com/fwlink/?LinkID=119298)Web サイトです。  
  
## <a name="see-also"></a>参照  
 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)