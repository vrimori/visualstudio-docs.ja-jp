---
title: シェル (分離または統合) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0001ff15bd6f74ea0b993c73a9c458d5724a28a7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266124"
---
# <a name="shell-isolated-or-integrated"></a>シェル (分離または統合)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

統合または分離モードでは、独自の Visual Studio ベースのアプリケーションを作成できます。 統合モードでは、多くの Visual Studio の機能は、アプリケーションだけでなく使用できます。 分離モードでは、独自の拡張機能と共に配布する Visual Studio の機能のサブセットを選択します。  
  
## <a name="integrated-mode"></a>統合モード  
 統合モードでは、ユーザーが、カスタム ツールと共に、Visual Studio の標準的な機能を使用することができるようにします。 統合シェルは、主にプログラミング言語とソフトウェア開発ツールをホストします。  
  
 統合シェルで自動的に構築されたカスタム ツールは、同じコンピューターにインストールされている Visual Studio の他の任意のエディションとマージします。 Visual Studio が既にインストールされていない場合は、Visual Studio の統合シェルの再頒布可能パッケージのバージョンを行うことができます。  
  
 Visual Studio の統合シェルの再頒布可能パッケージのバージョンでは、プログラミング言語と、それぞれのプロジェクト システムをサポートする機能は含まれません。  
  
> [!NOTE]
>  Visual Studio シェル統合モードは、Visual Studio Express edition 以外のすべてのエディションと共にインストールできます。  
  
 詳細については、次を参照してください。 [Visual Studio Shell (Integrated)](../extensibility/visual-studio-shell-integrated.md)します。  
  
## <a name="isolated-mode"></a>分離モード  
 分離モードでは、サイド バイ サイドで実行するカスタム ツールを作成できます。 Visual Studio の他のバージョン。 標準の Visual Studio のすべての機能に応じてなしの Visual Studio services にアクセスできるツールの主なものでは。 Visual Studio 分離シェルに基づいて構築されたアプリケーションの外観をカスタマイズすることができます。 簡単に、機能と、アプリケーションと共に表示されるたくないメニュー コマンドのグループをオフにできます。  
  
 詳細については、次を参照してください。 [Visual Studio 分離シェル](../extensibility/visual-studio-isolated-shell.md)します。  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>統合または分離シェル アプリケーションを配布  
 統合または分離シェル アプリケーションを配布するために、アプリケーションを特殊な統合または分離シェル再頒布可能パッケージ、およびインストール プログラムに含める必要があります。 配布とインストールの詳細については、次を参照してください。[分離シェル アプリケーションを配布する](../extensibility/distributing-isolated-shell-applications.md)します。  
  
> [!IMPORTANT]
>  [使用許諾契約書 (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552)シェルには Visual Studio 統合シェルと分離のデータ収集のセクションが含まれています (**セクション 3。データ**)。  これには、Microsoft によって、アプリケーションを作成するか、統合または分離シェル ソフトウェアのユーザーから収集する顧客の使用状況データについて説明します。 詳細については、次を参照してください。 [Microsoft Visual Studio 製品ファミリ プライバシーに関する声明](https://www.visualstudio.com/en-us/dn948229)します。  
>   
>  アプリケーションを使って、顧客から別の使用状況データを収集する場合は、収集するのアプリケーションのユーザーに適切な通知を提供する必要があります。  Visual Studio Software Development Kit のライセンス、に従って、アプリケーションの一部として分離または統合シェル ソフトウェアを配布するときに、次のいずれかを含める必要があります。  
>   
>  -   アプリケーション ライセンスの一部として、エンド ユーザー ライセンス契約  
> -   Visual Studio を保護する条項に同意する顧客を必要とする独自の EULA 統合または分離シェルのソフトウェアの Microsoft のエンド ユーザー ライセンス条項と少なくとも同じのシェル  
  
## <a name="additional-resources"></a>その他のリソース  
 再頒布可能パッケージの詳細については、次を参照してください。、 [Visual Studio 機能拡張ダウンロード](http://go.microsoft.com/fwlink/?LinkID=119298)Web サイト。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)

