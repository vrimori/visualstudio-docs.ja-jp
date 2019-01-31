---
title: '方法: 製品マニフェストを作成する |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39c24f35ec68fdfda173cf24d8018102a42ea81b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976551"
---
# <a name="how-to-create-a-product-manifest"></a>方法: 製品マニフェストを作成する
アプリケーションの必須コンポーネントを展開するには、ブートス トラップ パッケージを作成できます。 ブートス トラップ パッケージには、ロケールごとに、パッケージ マニフェストが 1 つの製品マニフェスト ファイルが含まれています。 パッケージ マニフェストには、パッケージのローカライズに固有の要素が含まれています。 これには、文字列、使用許諾契約書、および言語パックが含まれます。  
  
 マニフェストの製品の詳細については、次を参照してください。[方法。パッケージ マニフェストを作成する](../deployment/how-to-create-a-package-manifest.md)」を参照してください。  
  
## <a name="create-the-product-manifest"></a>製品マニフェストを作成します。  
  
#### <a name="to-create-the-product-manifest"></a>製品マニフェストを作成するには  
  
1.  ブートス トラップ パッケージ用のディレクトリを作成します。 この例では、C:\package を使用します。  
  
2.  Visual Studio で作成するという新しい XML ファイル*product.xml*、保存して、 *C:\package*フォルダー。  
  
3.  パッケージの XML 名前空間と製品コードを記述する次の XML を追加します。 製品コードをパッケージの一意の識別子に置き換えます。  
  
    ```xml  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  パッケージに依存関係があることを指定する XML を追加します。 この例では、Microsoft Windows インストーラー 3.1 の依存関係を使用します。  
  
    ```xml  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  ブートス トラップ パッケージに含まれるすべてのファイルを一覧表示の XML を追加します。 この例は、パッケージのファイル名を使用して*CorePackage.msi*します。  
  
    ```xml  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  コピーまたは移動、 *CorePackage.msi*ファイルを*C:\package*フォルダー。  
  
7.  ブートス トラップ コマンドを使用してパッケージをインストールする XML を追加します。 ブートス トラップが自動的に追加されます、 **/qn**フラグを *.msi*ファイルで、サイレント インストールされます。 ファイルの場合、 *.exe*、ブートス トラップの実行、 *.exe*シェルを使用してファイル。 次の XML には、引数にはない*CorePackage.msi*にコマンドライン引数を配置することができますが、`Arguments`属性。  
  
    ```xml  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  このブートス トラップ パッケージがインストールされていることを確認する次の XML を追加します。 製品コードを再頒布可能コンポーネントの GUID に置き換えます。  
  
    ```xml  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. ブートス トラップ コンポーネントが既にインストールされている場合は、に応じてブートス トラップの動作を変更する XML を追加します。 コンポーネントがインストールされている場合、ブートス トラップ パッケージは実行されません。 このコンポーネントは管理者特権を必要とするために、現在のユーザーに管理者がかどうか、次の XML を確認します。  
  
    ```xml  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. インストールが成功した場合と、再起動が必要な場合は、終了コードを設定する XML を追加します。 次の XML では、失敗して FailReboot 終了コードは、パッケージのインストールを続行がない、ブートス トラップすることを示すについて説明します。  
  
    ```xml  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. ブートス トラップ コマンドのセクションの末尾に次の XML を追加します。  
  
    ```xml  
        </Command>  
    </Commands>  
    ```  
  
12. 移動、 *C:\package*を Visual Studio ブートス トラップ ディレクトリのフォルダー。 これは Visual Studio 2010 の場合、 *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*ディレクトリ。  
  
## <a name="example"></a>例  
 製品マニフェストには、カスタムの必須コンポーネントのインストール手順が含まれています。  
  
```xml  
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