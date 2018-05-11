---
title: ブートス トラップ パッケージを作成します。
ms.custom: ''
ms.date: 05/02/2018
ms.technology: vs-ide-deployment
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
ms.openlocfilehash: 234f89f2d0a28c0836ee06df4c49c3ab60f102ce
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="create-bootstrapper-packages"></a>ブートス トラップ パッケージを作成します。
セットアップ プログラムは、Windows インストーラー (.msi) ファイルや実行可能プログラムなどの再頒布可能コンポーネントを検出およびインストールするように構成できる汎用的なインストーラーです。 インストーラーはブートストラップとも呼ばれます。 ブートストラップは、コンポーネントのインストールを管理するためのメタデータを指定する、一連の XML マニフェストによってプログラミングされます。  表示される各再頒布可能コンポーネント、または必要な前提条件、**の前提条件**ClickOnce のダイアログ ボックスは、ブートス トラップ パッケージです。 ブートストラップ パッケージは、必須コンポーネントのインストール方法を記述するマニフェスト ファイルを含むディレクトリおよびファイルのグループです。 
  
ブートストラップでは、まず、既にインストールされている必須コンポーネントがあるかどうかが検出されます。 必須コンポーネントがインストールされていない場合、ライセンス条項が表示されます。 次に、エンド ユーザーがライセンス条項に同意すると、必須コンポーネントのインストールが開始されます。 すべての必須コンポーネントが検出された場合は、そのままアプリケーション インストーラーが開始されます。  
  
## <a name="create-custom-bootstrapper-packages"></a>カスタム ブートス トラップ パッケージを作成します。  
ブートス トラップ マニフェストを生成するには、Visual Studio の XML エディターを使用します。 ブートス トラップ パッケージを作成する例を参照してください[チュートリアル: プライバシー プロンプトでのカスタム ブートス トラップの作成](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md)です。  
  
ブートス トラップ パッケージを作成するには、製品マニフェストを作成するして、各パッケージのマニフェストにも、コンポーネントのバージョンに合わせてローカライズします。
  
* 製品マニフェスト*product.xml*パッケージの言語に依存しないメタデータが含まれています。 再頒布可能コンポーネントのすべてのローカライズ バージョンに共通するメタデータが含まれます。  このファイルを作成するを参照してください。[する方法: 製品マニフェストを作成](../deployment/how-to-create-a-product-manifest.md)です。
  
* パッケージ マニフェスト*package.xml*、言語固有のメタデータを含むに通常ローカライズされたエラー メッセージが含まれています。 コンポーネントの各ローカライズ バージョンに対して、少なくとも 1 つのパッケージ マニフェストが必要です。 このファイルを作成するを参照してください。[する方法: パッケージ マニフェストを作成](../deployment/how-to-create-a-package-manifest.md)です。
  
これらのファイルが作成されたら、製品マニフェスト ファイルをカスタム ブートストラップ名のフォルダーに格納します。 パッケージ マニフェスト ファイルは、ロケール名のフォルダーに格納します。 たとえば、英語の再頒布用のパッケージ マニフェスト ファイルは、en というフォルダーに格納します。 日本語用は ja、ドイツ語用は de など、ロケールごとにこの手順を繰り返します。 最終的に、カスタム ブートストラップ パッケージは次のようなフォルダー構造になります。  

    ```
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
  
次に、再頒布可能パッケージのファイルをブートス トラップ フォルダーの場所にコピーします。 詳細については、「 [How to: Create a Localized Bootstrapper Package](../deployment/how-to-create-a-localized-bootstrapper-package.md)」を参照してください。
 
    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
    
または  
    
    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
  
ブートストラップ フォルダーの場所は、次のレジストリ キーの **Path** 値からも特定できます。  
  
    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*
  
64 ビット システムでは、次のレジストリ キーを使用します。  
  
    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*
  
再頒布可能コンポーネントは、パッケージのディレクトリの下の専用のサブフォルダーにそれぞれ表示されます。 製品マニフェストと再頒布可能ファイルはこのサブフォルダーに格納されます。 コンポーネントとパッケージ マニフェストのローカライズ版は、カルチャ名に従ってという名前のサブフォルダーに配置する必要があります。  
  
これらのファイルは、ブートス トラップ フォルダーにコピーした後、ブートス トラップ パッケージは、Visual Studio で自動的に表示されます**の前提条件** ダイアログ ボックス。 カスタム ブートス トラップ パッケージが表示されない場合を閉じてから開き、**の前提条件** ダイアログ ボックス。 詳細については、「 [Prerequisites Dialog Box](../ide/reference/prerequisites-dialog-box.md)」を参照してください。  
  
ブートストラップによって自動的に設定されるプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|ApplicationName|アプリケーションの名前。|  
|ProcessorArchitecture|実行可能ファイルが対象とするプラットフォームのプロセッサと、ワードあたりのビット数。 次の値があります。<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/en-us/library/aa372490\(v=vs.140\).aspx)|Microsoft Windows 95、Windows 98、または Windows ME の各オペレーティング システムのバージョン番号。 バージョンの構文は、Major.Minor.ServicePack です。|  
|[VersionNT](https://msdn.microsoft.com/en-us/library/aa372495\(v=vs.140\).xaspx)|Windows NT、Windows 2000、Windows XP、Windows Vista、Windows Server 2008、または Windows 7 の各オペレーティング システムのバージョン番号。 バージョンの構文は、Major.Minor.ServicePack です。|  
|[VersionMSI](https://msdn.microsoft.com/en-us/library/aa372493\(v=vs.140\).aspx)|インストール中に実行される Windows インストーラーのアセンブリ (msi.dll) のバージョン。|  
|[AdminUser](https://msdn.microsoft.com/en-us/library/aa367545\(v=vs.140\).aspx)|このプロパティは、ユーザーに管理者特権がある場合に設定されます。 値は true または false です。|  
|InstallMode|インストール モードは、コンポーネントのインストール元の場所を示します。 次の値があります。<br /><br /> -HomeSite - 前提条件は、製造元の Web サイトからインストールされます。<br />-SpecificSite - 前提条件は、選択した場所からインストールされます。<br />-SameSite - 前提条件は、アプリケーションと同じ場所からインストールされます。|  
  
## <a name="separating-redistributables-from-application-installations"></a>再配布可能コンポーネントとアプリケーションのインストールの分離  
再配布可能ファイルは、セットアップ プロジェクトで配置されないようにすることができます。 そのためには、.NET Framework ディレクトリの RedistList フォルダーに再頒布可能リストを作成します。  
  
`%ProgramFiles%\Microsoft.NET\RedistList`  
  
再頒布可能リストは XML ファイルです。このファイルには、 *Company Name*.*Component Name*.RedistList.xml という形式の名前を付けます。 そのため、たとえば、Acme 社製の Datawidgets というコンポーネントの場合、使用*Acme.DataWidgets.RedistList.xml*です。 再頒布可能リストの内容は、たとえば次のようになります。  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>関連項目  
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [前提条件 ダイアログ ボックス](../ide/reference/prerequisites-dialog-box.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)   
 [使用して、Visual Studio 2005 ブートス トラップが、インストールを開始します.](http://go.microsoft.com/fwlink/?LinkId=107537)