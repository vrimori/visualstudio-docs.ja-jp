---
title: カスタム スタート ページを展開する |Microsoft Docs
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
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e788f9bb1ca0333fd20237103cf6bce136af2e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795116"
---
# <a name="deploying-custom-start-pages"></a>カスタム スタート ページのデプロイ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 配置を使用するか、ターゲット コンピューター上の適切な場所にファイルをコピーして、カスタム スタート ページを展開することができます。  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>スタート ページ プロジェクト テンプレートを使用して VSIX 配置  
 スタート ページ プロジェクト テンプレートを使用して、[スタート] ページを作成し、プロジェクトをビルドすると、Visual Studio は、配布できる .vsix ファイルを作成します。 スタート ページで、.vsix ファイルをパッケージ化には、次のオプションによっては、対象の展開。  
  
- ネットワーク共有またはパブリック Web サイトでは、.vsix ファイルを配置できます。 ファイルを開く誰かと、スタート ページが自動的にインストールします。  
  
- .Vsix ファイルをアップロードすることができます、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトのユーザーを使用してインストールできるように**拡張機能マネージャー**します。  
  
  スタート ページ プロジェクト テンプレートは、コピーを変更して、元を保持するように Visual Studio スタート ページの既定のコピーを作成します。  
  
  使用して、スタート ページ プロジェクト テンプレートを取得する**拡張機能マネージャー**または Web サイトからダウンロードしています。  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>スタート ページ プロジェクト テンプレートを使用せず、VSIX 配置  
 VSIX 展開を成功させるには、VSIX の登録プロセスとで認識されているフォルダーにインストールする拡張機能が必要があります**拡張機能マネージャー**します。 スタート ページ プロジェクト テンプレートが既に適切なフォルダーを指定しますので、VSIX 配置の拡張機能をパッケージ化するときにそれを使用することをお勧めします。 ただし、場合は、テンプレートを使うことはできませんがある場合は、これを使用せず、VSIX 配置を作成できます。  
  
 スタート ページ プロジェクト テンプレートを使用せずには、VSIX の配置を作成するには、まずこれら 2 つの方法のいずれかで [スタート] ページの .vsix ファイルを作成します。  
  
- によって、カスタム スタート ページにファイルを空の VSIX プロジェクトに追加します。 詳細については、次を参照してください。 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)します。  
  
- .Vsix ファイルを手動で作成します。 詳細については、次を参照してください。[方法: 拡張機能 (VSIX 配置) を手動でパッケージ化](../misc/how-to-manually-package-an-extension-vsix-deployment.md)します。  
  
  Visual studio がスタート ページでは、認識、 `Content Element` VSIX マニフェストの含める必要があります、`CustomExtension Element`を持つ、`Type`属性に設定`"StartPage"`。 VSIX 配置を使用して、インストールされているスタート ページの拡張機能が表示されます、**スタート ページのカスタマイズ**ボックスの一覧、**スタートアップ**オプションのページとして **[インストールされている拡張機能]***拡張機能名*します。  
  
  スタート ページのパッケージには、アセンブリが含まれている場合、Visual Studio の起動時に使用可能なものには、パスの登録をバインディングを追加する必要があります。 これを行うには、パッケージが次の情報を持つ .pkgdef ファイルが含まれることを確認します。  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>すべてのユーザー用の VSIX 配置  
 既定では、VSIX パッケージ内に配置される拡張機能は、現在のユーザーに対してのみインストールします。 すべてのユーザーの展開の作成で、ターゲット マシンのすべてのユーザーのスタート ページのインストールを行うことができます。  
  
##### <a name="to-create-an-all-users-deployment"></a>すべてのユーザーの展開を作成するには  
  
1.  コード ビューでは、extension.vsixmanifest ファイルを開きます。  
  
2.  `Identifier` 、Vsix マニフェストの要素を追加、`AllUsers`要素の値を持つ`true`します。  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     これにより、管理者のアクセス許可を要求し、\Common7\IDE\Extensions にファイルをインストールするには、vsix インストーラーです。  
  
3.  .Pkgdef ファイルを開きます。  
  
4.  変更を次を追加することで hklm の既定のスタート ページを設定する .pkgdef、 *MyStartPage.xaml*のスタート ページを含む .xaml ファイルの名前を指定します。  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri「=」$PackageFolder$\\*MyStartPage.xaml*"  
  
     これは、新しいスタート ページの場所を検索する Visual 立ったを指示します。  
  
## <a name="file-copy-deployment"></a>ファイル コピーによる展開  
 カスタム スタート ページを配置する .vsix ファイルを作成する必要はありません。 代わりに、ユーザーの \StartPages\ フォルダーに直接、マークアップとサポート ファイルをコピーすることができます。 **スタート ページのカスタマイズ**ボックスの一覧、**スタートアップ**オプション ページには、パスと共に、そのフォルダー内のすべての .xaml ファイルが一覧表示されます-など %USERPROFILE%\My documents \visual Studio *バージョン*\StartPages\\*ファイル名*.xaml です。 スタート ページには、プライベート アセンブリへの参照が含まれている場合は、それらをコピーし、\PrivateAssemblies\ フォルダー内に 必要があります。  
  
 パッケージ化せずに作成するスタート ページを配布するには、.vsix ファイルで勧め基本的なファイルのコピー方法を使用することは、たとえば、バッチ スクリプト、またはその他の展開テクノロジすることができます、このファイルを必要なディレクトリに配置します。  
  
#### <a name="to-manually-install-a-custom-start-page"></a>カスタム スタート ページを手動でインストールするには  
  
1.  アセンブリ以外の任意のサポート ファイルと共に、スタート ページのマークアップを含む .xaml ファイルをコピーし、ユーザーの \StartPages\ フォルダーに貼り付けます。  
  
2.  スタート ページには、アセンブリが必要とする場合は、それらをコピーし、貼り付けることで.\\ *Visual Studio インストール フォルダー*\Common7\IDE\PrivateAssemblies\\します。  
  
3.  **スタート ページのカスタマイズ**ボックスの一覧、**スタートアップ**オプション ページで、新しいスタート ページを選択します。 詳細については、[スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)に関するページを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)   
 [スタート ページへのユーザー コントロールの追加](../extensibility/adding-user-control-to-the-start-page.md)

