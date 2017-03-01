---
title: "Shell (分離プロセスまたは統合) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ed0e82dbc2c093a94080fe3fcf07a3e3b20e1a50
ms.lasthandoff: 02/22/2017

---
# <a name="shell-isolated-or-integrated"></a>Shell (分離プロセスまたは統合)
統合または分離モードで Visual Studio ベース アプリケーションを作成することができます。 統合モードでは、多くの Visual Studio 機能をアプリケーションだけでなく使用します。 分離モードでは、独自の拡張機能と共に配布する Visual Studio の機能のサブセットを選択します。  
  
## <a name="integrated-mode"></a>統合モード  
 統合モードでは、カスタム ツールと同様に、Visual Studio の標準的な機能を使用するユーザー。 統合シェルは、プログラミング言語とソフトウェア開発ツールをホストするため、主に対象としています。  
  
 統合 shell で自動的に組み込まれているカスタムのツールは、同じコンピューターにインストールされている Visual Studio の他の任意のエディションとマージします。 Visual Studio が既にインストールされていない場合は、Visual Studio の統合シェルの再頒布可能パッケージのバージョンを提供できます。  
  
 Visual Studio の統合シェルの再頒布可能パッケージのバージョンでは、プログラミング言語とそれぞれのプロジェクト システムをサポートする機能は含まれません。  
  
> [!NOTE]
>  Visual Studio Express edition を除くのすべてのエディションと、Visual Studio シェル統合モードをインストールすることができます。  
  
 詳細については、次を参照してください。 [Visual Studio Shell (Integrated)](../extensibility/visual-studio-shell-integrated.md)します。  
  
## <a name="isolated-mode"></a>分離モード  
 分離モードでは、サイド バイ サイド実行するカスタム ツールを作成できます。 Visual Studio の他のバージョンとします。 標準の Visual Studio のすべての機能に応じてせず、Visual Studio のサービスにアクセスできるツールの主なものです。 Visual Studio の分離シェルに基づいて構築されたアプリケーションの外観をカスタマイズできます。 簡単に、機能とメニュー コマンドのグループ、アプリケーションと共に表示するたくないを無効にすることができます。  
  
 詳細については、次を参照してください。 [Visual Studio の分離シェル](../extensibility/visual-studio-isolated-shell.md)します。  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>統合または分離シェル アプリケーションを配布します。  
 統合または分離シェル アプリケーションを配布するためには、アプリケーションを特殊な統合型または分離シェル、再頒布可能インストール プログラムする必要があります。 配布とインストールの詳細については、次を参照してください。[分離シェル アプリケーションを配布する](../extensibility/distributing-isolated-shell-applications.md)です。  
  
> [!IMPORTANT]
>  [使用許諾契約 (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552)シェルには Visual Studio が統合されており、特定のデータの収集に関するセクションが含まれています (**セクション 3 です。Data**).  アプリケーションに組み込むか、統合型または分離シェル ソフトウェアのユーザーから収集マイクロソフトが顧客の使用状況データを説明します。 詳細については、次を参照してください。 [Microsoft Visual Studio の製品ファミリ プライバシーに関する声明](https://www.visualstudio.com/en-us/dn948229)します。  
>   
>  アプリケーションを顧客から別の使用状況データを収集する場合は、収集するのアプリケーションのユーザーに適切な通知を提供する必要があります。  Visual Studio ソフトウェア開発キット ライセンスに応じて、アプリケーションの一部として分離または統合シェル ソフトウェアを配布するときに、次のいずれかを含める必要があります。  
>   
>  -   アプリケーション ライセンスの一部として使用許諾契約書  
> -   顧客が Visual Studio の保護の条項に同意を必要とする独自の EULA 統合セキュリティまたはシェル ソフトウェア用の Microsoft のエンド ユーザー ライセンス条項と少なくとも同等シェルを分離  
  
## <a name="additional-resources"></a>その他のリソース  
 再頒布可能パッケージの詳細については、次を参照してください。、 [Visual Studio 機能拡張ダウンロード](http://go.microsoft.com/fwlink/?LinkID=119298)Web サイトです。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)
