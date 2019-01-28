---
title: カスタム スタート ページを展開する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e89ff96ef73070570b7295ab6256a501d5865b6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982768"
---
# <a name="deploy-custom-start-pages"></a>カスタム スタート ページをデプロイします。

VSIX 配置を使用するか、ターゲット コンピューター上の適切な場所にファイルをコピーして、カスタム スタート ページを展開することができます。

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>スタート ページ プロジェクト テンプレートを使用して VSIX 配置

Visual Studio をスタート ページ プロジェクト テンプレートを使用して、[スタート] ページを作成し、プロジェクトをビルドすると、作成、 *.vsix*ファイルを配布することができます。 パッケージを開始 ページで、 *.vsix*ファイルには、対象ユーザーにに応じて、デプロイに次のオプションが与えられます。

-   配置することができます、 *.vsix*ファイル、ネットワーク共有またはパブリック Web サイト。 ファイルを開く誰かと、スタート ページが自動的にインストールします。

-   アップロードすることができます、 *.vsix*ファイルを[Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=123847) Web サイトのユーザーを使用してインストールできるように**拡張機能マネージャー**します。

スタート ページ プロジェクト テンプレートは、コピーを変更して、元を保持するように Visual Studio スタート ページの既定のコピーを作成します。

使用して、スタート ページ プロジェクト テンプレートを取得する**拡張機能マネージャー**または Web サイトからダウンロードしています。

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>スタート ページ プロジェクト テンプレートを使用せず、VSIX 配置
 VSIX 展開を成功させるには、VSIX の登録プロセスとで認識されているフォルダーにインストールする拡張機能が必要があります**拡張機能マネージャー**します。 スタート ページ プロジェクト テンプレートが既に適切なフォルダーを指定しますので、VSIX 配置の拡張機能をパッケージ化するときにそれを使用することをお勧めします。 ただし、場合は、テンプレートを使うことはできませんがある場合は、これを使用せず、VSIX 配置を作成できます。

 スタート ページ プロジェクト テンプレートを使用せずには、VSIX 配置を作成するに最初に作成、 *.vsix*これら 2 つの方法のいずれかで [スタート] ページのファイル。

- によって、カスタム スタート ページにファイルを空の VSIX プロジェクトに追加します。 詳細については、次を参照してください。 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)します。

- 手動で作成、 *.vsix*ファイル。 作成する、 *.vsix*ファイルを手動で。

  1.  作成、 *extension.vsixmanifest*ファイルと *[Content_Types] .xml*新しいフォルダー内のファイル。 詳細については、次を参照してください。 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)します。

  2.  Windows エクスプ ローラーでは、2 つの XML ファイルを含むフォルダーを右クリックし、をクリックして**送信**圧縮 (zip 形式) フォルダーを順にクリックします。 結果の名前を変更 *.zip*ファイルを*Filename.vsix*ファイル名は、パッケージをインストールする再頒布可能ファイルの名前です。

  Visual studio がスタート ページでは、認識、 `Content Element` VSIX マニフェストの含める必要があります、`CustomExtension Element`を持つ、`Type`属性に設定`"StartPage"`。 VSIX 配置を使用して、インストールされているスタート ページの拡張機能が表示されます、**スタート ページのカスタマイズ**ボックスの一覧、**スタートアップ**オプションのページとして **[インストールされている拡張機能]** *拡張機能名*します。

  スタート ページのパッケージには、アセンブリが含まれている場合、Visual Studio の起動時に使用可能なものには、パスの登録をバインディングを追加する必要があります。 これを行うことをパッケージが含まれていることを確認して、 *.pkgdef*次の情報を含むファイル。

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>すべてのユーザー用の VSIX 配置
 既定では、VSIX パッケージ内に配置される拡張機能は、現在のユーザーに対してのみインストールします。 すべてのユーザーの展開の作成で、ターゲット マシンのすべてのユーザーのスタート ページのインストールを行うことができます。

### <a name="to-create-an-all-users-deployment"></a>すべてのユーザーの展開を作成するには

1.  開く、 *extension.vsixmanifest*コード ビューでのファイル。

2.  `Identifier` 、Vsix マニフェストの要素を追加、`AllUsers`要素の値を持つ`true`します。

    ```
    <AllUsers>true</AllUsers>
    ```

     これにより、管理者のアクセス許可を要求し、ファイルをインストールするには、vsix インストーラー *\Common7\IDE\Extensions* します。

3.  開く、 *.pkgdef*ファイル。

4.  変更、 *.pkgdef* 、次を追加することで、hklm の既定のスタート ページを設定する場所*MyStartPage.xaml*の名前を指定します、 *.xaml*開始を含むファイルページです。

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     これにより、Visual Studio に新しいスタート ページの場所を検索するように指示します。

## <a name="file-copy-deployment"></a>ファイル コピーによる展開
 作成する必要はありません、 *.vsix*カスタム スタート ページを配置するファイル。 マークアップは、サポートには、ユーザーの直接ファイルをコピーする代わりに、 <em>\StartPages\*フォルダー。**スタート ページのカスタマイズ</em>* ボックスの一覧、**スタートアップ**オプション ページではすべて *.xaml*パスと共に、そのフォルダー内のファイル-たとえば、 *%USERPROFILE%\My documents \visual Studio {バージョン} \StartPages\\{ファイル名} .xaml*します。 それらをコピーして貼り付けるにする必要がありますのスタート ページには、プライベート アセンブリへの参照が含まれている場合、* \PrivateAssemblies\*フォルダー。

 パッケージ化することで作成したスタートのページを配布する、 *.vsix*バッチ スクリプトなどの基本的なファイル コピー戦略を使用することもできるようにするその他の展開テクノロジ ファイルを配置することお勧めするファイル、必要なディレクトリ。

### <a name="to-manually-install-a-custom-start-page"></a>カスタム スタート ページを手動でインストールするには

1.  コピー、 *.xaml*ファイルをアセンブリ以外の任意のサポート ファイルと共に、スタート ページ マークアップを格納し、ユーザーの貼り付けます * \StartPages\*フォルダー。

2.  スタート ページは、アセンブリを必要とする場合、コピーし、貼り付けることで *.\\{Visual Studio インストール フォルダー} \Common7\IDE\PrivateAssemblies\\*します。

3.  **スタート ページのカスタマイズ**ボックスの一覧、**スタートアップ**オプション ページで、新しいスタート ページを選択します。 詳細については、次を参照してください。[スタート ページをカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)します。

## <a name="see-also"></a>関連項目

- [スタート ページのカスタマイズ](../ide/customizing-the-start-page-for-visual-studio.md)
- [スタート ページにユーザー コントロールを追加します。](../extensibility/adding-user-control-to-the-start-page.md)