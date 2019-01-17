---
title: ブートストラップ パッケージの作成
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 158befc5b401feb700a2effff7378b1edac6a2c9
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "53878391"
---
# <a name="create-bootstrapper-packages"></a>ブートストラップ パッケージの作成
セットアップ プログラムは、Windows インストーラー (*.msi*) ファイルや実行可能プログラムなどの再頒布可能コンポーネントを検出およびインストールするように構成できる汎用的なインストーラーです。 インストーラーはブートストラップとも呼ばれます。 ブートストラップは、コンポーネントのインストールを管理するためのメタデータを指定する、一連の XML マニフェストによってプログラミングされます。  表示される各コンポーネントの再頒布可能パッケージ、または前提条件、**の前提条件**ClickOnce のダイアログ ボックスは、ブートス トラップ パッケージです。 ブートストラップ パッケージは、必須コンポーネントのインストール方法を記述するマニフェスト ファイルを含むディレクトリおよびファイルのグループです。 
  
ブートストラップでは、まず、既にインストールされている必須コンポーネントがあるかどうかが検出されます。 必須コンポーネントがインストールされていない場合、ライセンス条項が表示されます。 次に、エンド ユーザーがライセンス条項に同意すると、必須コンポーネントのインストールが開始されます。 すべての必須コンポーネントが検出された場合は、そのままアプリケーション インストーラーが開始されます。  
  
## <a name="create-custom-bootstrapper-packages"></a>カスタム ブートス トラップ パッケージを作成します。  
ブートス トラップ マニフェストを生成するには、Visual Studio での XML エディターを使用します。 ブートス トラップ パッケージを作成する例を表示するには、次を参照してください。[チュートリアル。プライバシー プロンプトを使用のカスタム ブートス トラップの作成](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)です。  
  
ブートス トラップ パッケージを作成するに製品マニフェストを作成し、各パッケージのマニフェストにも、コンポーネントのバージョンのローカライズされました。
  
* 製品マニフェスト、 *product.xml*パッケージの言語に依存しないメタデータが含まれています。 再頒布可能コンポーネントのすべてのローカライズ バージョンに共通するメタデータが含まれます。  このファイルを作成するを参照してください。[方法。製品マニフェストを作成する](../deployment/how-to-create-a-product-manifest.md)
  
* パッケージ マニフェストの*package.xml*、言語固有のメタデータを含む通常ローカライズされたエラー メッセージが含まれます。 コンポーネントの各ローカライズ バージョンに対して、少なくとも 1 つのパッケージ マニフェストが必要です。 このファイルを作成するを参照してください。[方法。パッケージ マニフェストを作成する](../deployment/how-to-create-a-package-manifest.md)
  
これらのファイルが作成されたら、製品マニフェスト ファイルをカスタム ブートストラップ名のフォルダーに格納します。 パッケージ マニフェスト ファイルは、ロケール名のフォルダーに格納します。 たとえば、英語の再頒布用のパッケージ マニフェスト ファイルは、en というフォルダーに格納します。 日本語用は ja、ドイツ語用は de など、ロケールごとにこの手順を繰り返します。 最終的に、カスタム ブートストラップ パッケージは次のようなフォルダー構造になります。  

    ```xml
    CustomBootstrapperPackage
      product.xml
      CustomBootstrapper.msi
      de
        eula.rtf
        package.xml
      en
        eula.rtf
        package.xml
      ja
        eula.rtf
        package.xml
    ```
  
次に、ブートス トラップ フォルダーの場所に再頒布可能ファイルをコピーします。 詳細については、「[方法 :ローカライズ版のブートストラップ パッケージを作成する](../deployment/how-to-create-a-localized-bootstrapper-package.md)」を参照してください。
 
    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
    
または  
    
    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
  
ブートストラップ フォルダーの場所は、次のレジストリ キーの **Path** 値からも特定できます。  
  
    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*
  
64 ビット システムでは、次のレジストリ キーを使用します。  
  
    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*
  
再頒布可能コンポーネントは、パッケージのディレクトリの下の専用のサブフォルダーにそれぞれ表示されます。 製品マニフェストで、再頒布可能ファイルの必要がありますが、このサブフォルダーに格納します。 コンポーネントとパッケージ マニフェストのローカライズ版は、カルチャ名に従ってという名前のサブフォルダーに配置する必要があります。  
  
これらのファイルをブートストラップ フォルダーにコピーすると、Visual Studio の **[必須コンポーネント]** ダイアログ ボックスにブートストラップ パッケージが自動的に表示されます。 カスタム ブートストラップ パッケージが表示されない場合は、**[必須コンポーネント]** ダイアログ ボックスを閉じてから開き直してください。 詳細については、「[[必須コンポーネント] ダイアログ ボックス](../ide/reference/prerequisites-dialog-box.md)」を参照してください。  
  
ブートストラップによって自動的に設定されるプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|ApplicationName|アプリケーションの名前。|  
|ProcessorArchitecture|実行可能ファイルが対象とするプラットフォームのプロセッサと、ワードあたりのビット数。 次の値があります。<br /><br /> -   Intel<br />-   IA64<br />-   AMD64|  
|[Version9x](/windows/desktop/Msi/version9x)|Microsoft Windows 95、Windows 98、または Windows ME の各オペレーティング システムのバージョン番号。 バージョンの構文は、Major.Minor.ServicePack です。|  
|[VersionNT](/windows/desktop/Msi/versionnt)|Windows NT、Windows 2000、Windows XP、Windows Vista、Windows Server 2008、または Windows 7 の各オペレーティング システムのバージョン番号。 バージョンの構文は、Major.Minor.ServicePack です。|  
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Windows インストーラーのアセンブリ (msi.dll) のインストール中に実行するのバージョン。|  
|[AdminUser](/windows/desktop/Msi/adminuser)|このプロパティは、ユーザーに管理者特権がある場合に設定されます。 値は true または false です。|  
|InstallMode|インストール モードは、コンポーネントのインストール元の場所を示します。 次の値があります。<br /><br /> -   HomeSite - ベンダーの Web サイトから必須コンポーネントをインストールします。<br />-   SpecificSite - 選択した場所から必須コンポーネントをインストールします。<br />-   SameSite - アプリケーションと同じ場所から必須コンポーネントをインストールします。|  
  
## <a name="separate-redistributables-from-application-installations"></a>アプリケーションのインストールから独立した再頒布可能パッケージ  
再配布可能ファイルは、セットアップ プロジェクトで配置されないようにすることができます。 そのためには、.NET Framework ディレクトリの RedistList フォルダーに再頒布可能リストを作成します。  
  
`%ProgramFiles%\Microsoft.NET\RedistList`  
  
再頒布可能リストは、次の形式の名前を XML ファイルです。*\<会社名 >。\<コンポーネント名 >。です*します。 たとえば、Acme 社製の DataWidgets というコンポーネントの場合は、*Acme.DataWidgets.RedistList.xml* にします。 再頒布可能リストの内容は、たとえば次のようになります。  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>関連項目  
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [[必須コンポーネント]](../ide/reference/prerequisites-dialog-box.md) ダイアログ ボックス   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)   
 [Visual Studio 2005 ブートストラップを使用してインストールを促進する](http://go.microsoft.com/fwlink/?LinkId=107537)
