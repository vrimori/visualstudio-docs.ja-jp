---
title: "方法: 製品マニフェストを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "依存関係, カスタム ブートストラップ パッケージ"
  - "必要条件, カスタム ブートストラップ パッケージ"
  - "製品ファイル [ClickOnce]"
  - "製品ファイル [Windows インストーラー]"
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法: 製品マニフェストを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アプリケーションの必須コンポーネントを配置するには、ブートストラップ パッケージを作成します。  ブートストラップ パッケージには、1 つの製品マニフェスト ファイルだけでなく、各ロケールのパッケージ マニフェストも含まれます。  パッケージ マニフェストには、パッケージのローカリゼーション固有の特性も含まれます。  これには、文字列、ライセンス条項、Language Pack などがあります。  
  
 製品マニフェストの詳細については、「[方法: パッケージ マニフェストを作成する](../deployment/how-to-create-a-package-manifest.md)」を参照してください。  
  
## 製品マニフェストの作成  
  
#### 製品マニフェストを作成するには  
  
1.  ブートストラップ パッケージのディレクトリを作成します。  この例では、C:\\package を使用します。  
  
2.  Visual Studio で、`product.xml` という新しい XML ファイルを作成し、C:\\package フォルダーに保存します。  
  
3.  次の XML を追加して、パッケージの XML 名前空間と製品コードを記述します。  製品コードは、パッケージの一意識別子に置き換えてください。  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  パッケージに依存関係があることを指定する XML を追加します。  この例では、Microsoft Windows インストーラー 3.1 への依存関係を使用します。  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  ブートストラップ パッケージ内にあるすべてのファイルを列挙する XML を追加します。  この例では、CorePackage.msi というパッケージ ファイル名を使用します。  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  CorePackage.msi ファイルを C:\\package フォルダーにコピーまたは移動します。  
  
7.  ブートストラップ コマンドを使用して、パッケージをインストールする XML を追加します。  ブートストラップは .msi ファイルに自動的に **\/qn** フラグを追加するため、サイレント インストールが実行されることになります。  ファイルが .exe の場合、ブートストラップはシェルを使用して .exe ファイルを実行します。  次の XML では CorePackage.msi への引数はありませんが、Arguments 属性にコマンド ライン引数を指定できます。  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  このブートストラップ パッケージがインストールされているかどうかをチェックする次の XML を追加します。  製品コードを再頒布可能コンポーネントの GUID に置き換えます。  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. ブートストラップ コンポーネントが既にインストールされているかどうかによって、ブートストラップの動作を変更する XML を追加します。  コンポーネントがインストールされている場合、ブートストラップ パッケージは実行されません。  このコンポーネントには管理特権が必要であるため、次の XML では、現在のユーザーが管理者かどうかをチェックしています。  
  
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
  
10. インストールが正常終了した場合と再起動が必要な場合の終了コードを設定する XML を追加します。  次の XML は、パッケージのインストールを続行しないことを示す Fail および FailReboot の終了コードの例です。  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. 次の XML を追加して、ブートストラップ コマンドのセクションを終了します。  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. C:\\package フォルダーを Visual Studio ブートストラップ ディレクトリに移動します。  Visual Studio 2010 の場合、これは \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages ディレクトリです。  
  
## 使用例  
 製品マニフェストには、カスタムの必須コンポーネントのインストール指示が含まれます。  
  
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
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)