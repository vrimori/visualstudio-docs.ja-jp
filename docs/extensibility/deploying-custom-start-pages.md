---
title: "カスタム スタート ページを展開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 21
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
ms.openlocfilehash: 9e99f022f1dec71b82c2261cae1d45705fe8dc7f
ms.lasthandoff: 02/22/2017

---
# <a name="deploying-custom-start-pages"></a>カスタム スタート ページを展開します。
VSIX 配置を使用するか、対象のコンピュータの正しい場所にファイルをコピーして、カスタム スタート ページを展開することができます。  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>[スタート] ページのプロジェクト テンプレートを使用して VSIX 配置  
 スタート ページのプロジェクト テンプレートを使用して、[スタート] ページを作成し、プロジェクトをビルドすると、Visual Studio は、配布できる .vsix ファイルを作成します。 展開は対象に応じて、次のオプションには、[スタート] ページで .vsix ファイルをパッケージ化します。  
  
-   ネットワーク共有またはパブリック Web サイト上には、.vsix ファイルを配置することができます。 ファイルを開いたとき、スタート ページが自動的にインストールします。  
  
-   .Vsix ファイルをアップロードする、 [Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトのユーザーを使用してインストールできるようにする**拡張機能マネージャー**します。  
  
 スタート ページのプロジェクト テンプレートは、そのコピーを変更したり、元の維持できるように、Visual Studio スタート ページの既定のコピーを作成します。  
  
 使用して、[スタート] ページでプロジェクト テンプレートを取得できます**拡張機能マネージャー**または Web サイトからダウンロードしています。  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>[スタート] ページのプロジェクト テンプレートを使用せずに VSIX 配置  
 VSIX の展開を成功させるには、VSIX の登録プロセスで、認識されているフォルダーにインストールする拡張機能が必要です**拡張機能マネージャー**します。 スタート ページのプロジェクト テンプレートが既に適切なフォルダーを指定するので、VSIX 配置の拡張機能をパッケージ化するときにそれを使用することをお勧めします。 ただし、テンプレートを使用できない場合がある場合は、それを使用せず、VSIX 配置を作成できます。  
  
 スタート ページのプロジェクト テンプレートを使用せずには、VSIX の配置を作成するに最初にこれら&2; つの方法のいずれかで [スタート] ページの .vsix ファイルを作成します。  
  
-   で、カスタム スタート ページにファイルを空の VSIX プロジェクトに追加します。 詳細については、次を参照してください。 [VSIX プロジェクトのテンプレート](../extensibility/vsix-project-template.md)します。  
  
-   .Vsix ファイルに手動で作成します。 詳細については、次を参照してください。[方法: 拡張機能 (VSIX 配置) を手動でパッケージ化](../misc/how-to-manually-package-an-extension-vsix-deployment.md)します。  
  
 Visual studio がスタート ページでは、認識、 `Content Element` VSIX マニフェストの含める必要があります、`CustomExtension Element`を持つ、`Type`属性に設定`"StartPage"`します。 VSIX の展開を使用してインストールされているスタート ページの拡張に表示される、**スタート ページのカスタマイズ**ボックスの一覧で、**スタートアップ**オプションのページとして**[インストールされている拡張機能]** *拡張機能名*します。  
  
 スタート ページにパッケージには、アセンブリが含まれている場合は、Visual Studio の起動時にそれらが使用できるようにバインド パスの登録を追加する必要があります。 これを行うには、次の情報を持つ .pkgdef ファイルがパッケージに含まれていることを確認します。  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>すべてのユーザー用の VSIX 配置  
 既定では、VSIX パッケージで配置される拡張機能は、現在のユーザーに対してのみインストールします。 対象コンピューターのすべてのユーザーのスタート ページにインストールを行うには、すべてのユーザーの展開を作成します。  
  
##### <a name="to-create-an-all-users-deployment"></a>すべてのユーザーの展開を作成するには  
  
1.  コード ビューでは、extension.vsixmanifest ファイルを開きます。  
  
2.  `Identifier` Vsix マニフェストの要素を追加、`AllUsers`要素の値を持つ`true`です。  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     これにより、\Common7\IDE\Extensions をファイルをインストールし、管理者のアクセス許可を要求するには、vsix インストーラーです。  
  
3.  .Pkgdef ファイルを開きます。  
  
4.  変更を次を追加することで、HKLM の下の既定のスタート ページを設定する .pkgdef、 *MyStartPage.xaml*をスタート ページを含む .xaml ファイルの名前を指定します。  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri「=」$PackageFolder$\\*MyStartPage.xaml*"  
  
     これは、新しいスタート ページの場所を検索するビジュアルの正式名称を示しています。  
  
## <a name="file-copy-deployment"></a>ファイル コピーによる展開  
 カスタム スタート ページをデプロイする .vsix ファイルを作成する必要はありません。 代わりに、ユーザーの \StartPages\ フォルダーに直接マークアップとサポート ファイルをコピーすることができます。 **スタート ページのカスタマイズ**ボックスの一覧で、**スタートアップ**オプション ページで、パスと共に、そのフォルダー内の各 .xaml ファイルを一覧表示-%USERPROFILE%\My documents \visual Studio 例えば*バージョン*\StartPages\\*ファイル名*.xaml です。 スタート ページには、プライベート アセンブリへの参照が含まれている場合は、それらをコピーして \PrivateAssemblies\ フォルダーに貼り付けること必要があります。  
  
 パッケージ化せずに作成するスタート ページを配布するには、.vsix ファイルでお勧め基本的なファイル コピー方法を使用することは、たとえば、バッチ スクリプトでは、またはを使用すると、他の展開テクノロジ、このファイルを必要なディレクトリに配置します。  
  
#### <a name="to-manually-install-a-custom-start-page"></a>カスタム スタート ページを手動でインストールするには  
  
1.  アセンブリ以外の任意のサポート ファイルと共に、スタート ページ マークアップを含む .xaml ファイルをコピーして、ユーザーの \StartPages\ フォルダーに貼り付けます。  
  
2.  スタート ページには、アセンブリが必要とする場合は、それらをコピーし、貼り付けることで.\\ *Visual Studio インストール フォルダー*\Common7\IDE\PrivateAssemblies\\します。  
  
3.  **スタート ページのカスタマイズ**ボックスの一覧で、**スタートアップ**オプション ページで、新しい [スタート] ページを選択します。 詳細については、次を参照してください。[スタート ページをカスタマイズする](../ide/customizing-the-start-page-for-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目  
 [スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)   
 [スタート ページにユーザー コントロールを追加します。](../extensibility/adding-user-control-to-the-start-page.md)
