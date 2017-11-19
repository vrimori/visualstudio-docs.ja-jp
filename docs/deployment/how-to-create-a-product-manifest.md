---
title: "方法: 製品マニフェストを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 36f1c1d5255233f57f7c2e266fe26fd8cbf789ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-product-manifest"></a>方法: 製品マニフェストを作成する
アプリケーションの前提条件を展開するには、ブートス トラップ パッケージを作成できます。 ブートス トラップ パッケージには、ロケールごとに、パッケージ マニフェストが 1 つの製品マニフェスト ファイルが含まれています。 パッケージ マニフェストには、パッケージのローカライズに固有の要素が含まれています。 これには、文字列、使用許諾契約書、および言語パックが含まれます。  
  
 製品マニフェストの詳細については、次を参照してください。[する方法: パッケージ マニフェストを作成](../deployment/how-to-create-a-package-manifest.md)です。  
  
## <a name="creating-the-product-manifest"></a>製品マニフェストを作成します。  
  
#### <a name="to-create-the-product-manifest"></a>製品マニフェストを作成するには  
  
1.  ブートス トラップ パッケージのディレクトリを作成します。 この例では、C:\package を使用します。  
  
2.  Visual Studio と呼ばれる新しい XML ファイルを作成`product.xml`、C:\package フォルダーに保存します。  
  
3.  パッケージの XML 名前空間と製品コードを記述する次の XML を追加します。 製品コードをパッケージの一意の識別子に置き換えます。  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  パッケージに依存関係があることを指定する XML を追加します。 この例では、Microsoft Windows インストーラー 3.1 の依存関係を使用します。  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  ブートス トラップ パッケージ内にあるすべてのファイルを列挙する XML を追加します。 この例では、パッケージのファイル名 CorePackage.msi を使用します。  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  コピーまたは CorePackage.msi ファイルを C:\package フォルダーに移動します。  
  
7.  ブートス トラップ コマンドを使用してパッケージをインストールする XML を追加します。 ブートス トラップを自動的に追加、 **/qn**フラグを .msi ファイルをサイレント インストールされます。 ファイルが .exe の場合は、ブートス トラップは、シェルを使用して、.exe ファイルを実行します。 次の XML に CorePackage.msi、引数はありませんが、Arguments 属性にコマンドライン引数を配置することができます。  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  このブートス トラップ パッケージがインストールされているかどうかはチェックは、次の XML を追加します。 製品コードを再頒布可能コンポーネントの GUID に置き換えます。  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. ブートス トラップ コンポーネントが既にインストールされている場合は、によってブートス トラップの動作を変更する XML を追加します。 コンポーネントがインストールされている場合、ブートス トラップ パッケージは実行されません。 次の XML では、このコンポーネントには、管理者特権が必要とするために、現在のユーザーが管理者がかどうかを確認します。  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. インストールが成功した場合と、再起動が必要な場合は、終了コードを設定する XML を追加します。 次の XML では、失敗して FailReboot 終了するブートス トラップは続行されませんパッケージをインストールすることを示すコードを示します。  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. ブートス トラップ コマンドについては、セクションの末尾に次の XML を追加します。  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. C:\package フォルダーを Visual Studio ブートス トラップ ディレクトリに移動します。 Visual Studio 2010 の場合、これは、\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages ディレクトリです。  
  
## <a name="example"></a>例  
 製品マニフェストには、カスタムの必須コンポーネントのインストール手順が含まれています。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>関連項目  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)