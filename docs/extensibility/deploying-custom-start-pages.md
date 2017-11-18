---
title: "カスタム スタート ページを展開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2217b77116ea561c32e96fcb7b92b520e680025
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-custom-start-pages"></a>カスタム スタート ページを展開します。
VSIX 配置を使用するか、ターゲット コンピューター上の適切な場所にファイルをコピーして、カスタム スタート ページを展開することができます。  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>スタート ページ プロジェクト テンプレートを使用して VSIX 配置  
 スタート ページ プロジェクト テンプレートを使用して、スタート ページを作成し、プロジェクトをビルドすると、Visual Studio は、配布できる .vsix ファイルを作成します。 .Vsix ファイルにスタート ページのパッケージ化、展開については、対象に応じて、次のオプションが与えられます。  
  
-   ネットワーク共有またはパブリック Web サイト上、.vsix ファイルを配置することができます。 ファイルを開いたとき、スタート ページが自動的にインストールします。  
  
-   探し、.vsix ファイルをアップロードすることができます、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトのユーザーを使用してインストールできるようにする**拡張機能マネージャー**です。  
  
 スタート ページ プロジェクト テンプレートは、コピーを変更したり、元の維持できるように、既定の Visual Studio スタート ページのコピーを作成します。  
  
 使用して、スタート ページ プロジェクト テンプレートを取得する**拡張機能マネージャー**または Web サイトからダウンロードしています。  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>スタート ページ プロジェクト テンプレートを使用せず、VSIX 配置  
 VSIX 展開を成功させるには、VSIX 登録プロセスによって、認識されているフォルダーにインストールする拡張機能が必要です**拡張機能マネージャー**です。 スタート ページ プロジェクト テンプレートが既に適切なフォルダーを指定するための拡張機能を VSIX 展開パッケージ化するには必ずそれを使用することをお勧めします。 ただし、場合は、テンプレートを使うことはできませんがある場合は場合、は、これを使用せず、VSIX の配置を作成できます。  
  
 スタート ページ プロジェクト テンプレートを使用せずには、VSIX の配置を作成するには、まず、.vsix ファイルをこれら 2 つの方法のいずれかで [スタート] ページの作成します。  
  
-   カスタム スタート ページのファイルを空の VSIX プロジェクトに追加します。 詳細については、次を参照してください。 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)です。  
  
-   .Vsix ファイルに手動で作成します。 .Vsix ファイルを手動で作成するには。  
    
    1.  新しいフォルダーになる extension.vsixmanifest ファイルと [Content_Types] .xml ファイルを作成します。 詳細については、次を参照してください。 [VSIX パッケージの構造は](/visualstudio/extensibility/anatomy-of-a-vsix-package)します。  
  
    2.  Windows エクスプローラで、2 つの XML ファイルを含むフォルダーを右クリックし、クリックを送信すると、および [圧縮 (zip 形式) フォルダー] をクリックします。 Filename.vsix、ファイル名は、パッケージをインストールする再頒布可能ファイルの名前を指定する、結果として得られる .zip ファイルの名前を変更します。  
  
 Visual Studio で、スタート ページを認識するため、 `Content Element` VSIX マニフェストの必要があります、`CustomExtension Element`を持つ、`Type`属性に設定`"StartPage"`です。 VSIX 展開を使用してインストールされているスタート ページの拡張に表示される、**スタート ページのカスタマイズ**ボックスの一覧、**スタートアップ**オプションのページとして**[インストールされている拡張機能]***拡張機能名*です。  
  
 スタート ページのパッケージには、アセンブリが含まれている場合は、Visual Studio の起動時に使用されるようにバインド パスの登録を追加する必要があります。 これを行うには、.pkgdef ファイル、次の情報を持つにはが、パッケージに含まれていることを確認します。  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>すべてのユーザー用の VSIX 配置  
 既定では、VSIX パッケージで配置される拡張機能は、現在のユーザーに対してのみインストールします。 すべてユーザー展開を作成することで、ターゲット コンピューターのすべてのユーザーのスタート ページにインストールを行うことができます。  
  
##### <a name="to-create-an-all-users-deployment"></a>すべてのユーザーの展開を作成するには  
  
1.  コード ビューでは、extension.vsixmanifest ファイルを開きます。  
  
2.  `Identifier` Vsix マニフェストの要素を追加、`AllUsers`要素の値を持つ`true`します。  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     これにより、管理者のアクセス許可を要求し、ファイルをインストールして、\Common7\IDE\Extensions を vsix インストーラーです。  
  
3.  .Pkgdef ファイルを開きます。  
  
4.  次のように追加することで、[HKLM] で、既定のスタート ページを設定する .pkgdef の変更場所*MyStartPage.xaml*をスタート ページを含む .xaml ファイルの名前を指定します。  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri「=」$PackageFolder$\\*MyStartPage.xaml*"  
  
     これは、新しいスタート ページの場所を検索する Visual 縦を示しています。  
  
## <a name="file-copy-deployment"></a>ファイル コピーによる展開  
 カスタム スタート ページを配置する .vsix ファイルを作成する必要はありません。 代わりに、ユーザーの \StartPages\ フォルダーに直接マークアップおよびサポート ファイルをコピーすることができます。 **スタート ページのカスタマイズ**ボックスの一覧、**スタートアップ**オプション ページには、パスと共に、そのフォルダー内のすべての .xaml ファイルが一覧表示されます — たとえば、%USERPROFILE%\My documents \visual Studio *バージョン*\StartPages\\*ファイル名*.xaml です。 スタート ページには、プライベート アセンブリへの参照が含まれている場合は、\PrivateAssemblies\ フォルダー内に貼り付けることしにコピーする必要があります。  
  
 パッケージ化せずに作成するスタート ページを配布するには、ことで、.vsix ファイルをお勧め基本的なファイルのコピー方法を使用することは、たとえば、バッチ スクリプト、またはその他の展開テクノロジできるようにする、このファイルを必要なディレクトリに配置します。  
  
#### <a name="to-manually-install-a-custom-start-page"></a>カスタム スタート ページを手動でインストールするには  
  
1.  アセンブリ以外の任意のサポート ファイルと共に、スタート ページのマークアップを含む .xaml ファイルをコピーし、ユーザーの \StartPages\ フォルダーに貼り付けます。  
  
2.  スタート ページには、アセンブリが必要とする場合は、それらをコピーし、貼り付けることで.\\ *Visual Studio インストール フォルダー*\Common7\IDE\PrivateAssemblies\\です。  
  
3.  **スタート ページのカスタマイズ**ボックスの一覧、**スタートアップ**オプション ページで、新しいスタート ページを選択します。 詳細については、次を参照してください。[スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)   
 [スタート ページへのユーザー コントロールの追加](../extensibility/adding-user-control-to-the-start-page.md)