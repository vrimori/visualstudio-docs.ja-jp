---
title: "方法: パッケージ マニフェストを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "パッケージ ファイル [ClickOnce]"
  - "パッケージ ファイル [Windows インストーラー]"
  - "必要条件, カスタム ブートストラップ パッケージ"
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: パッケージ マニフェストを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

アプリケーションの必須コンポーネントを配置するには、ブートストラップ パッケージを使用します。  ブートストラップ パッケージには、1 つの製品マニフェスト ファイルだけでなく、各ロケールのパッケージ マニフェストも含まれます。  複数のローカライズ バージョンに共通する機能は、製品マニフェストに含めます。  
  
 パッケージ マニフェストの詳細については、「[方法: 製品マニフェストを作成する](../deployment/how-to-create-a-product-manifest.md)」を参照してください。  
  
## パッケージ マニフェストの作成  
  
#### パッケージ マニフェストを作成するには  
  
1.  ブートストラップ パッケージのディレクトリを作成します。  この例では、C:\\package を使用します。  
  
2.  ロケール名のサブディレクトリ \(English など\) を作成します。  
  
3.  Visual Studio で、`package.xml` という XML ファイルを作成し、C:\\package\\en フォルダーに保存します。  
  
4.  ブートストラップ パッケージの名前、このローカライズされたパッケージ マニフェストのカルチャ、およびオプションのライセンス条項を列挙する XML を追加します。  次の XML では、`DisplayName` および `Culture` という変数を使用しています。これらの変数は、後で説明する要素によって定義されます。  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  ロケール固有のディレクトリ内にあるすべてのファイルを列挙する XML を追加します。  次の XML では、**en** ロケールに適用できる eula.txt というファイルを使用します。  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  ブートストラップ パッケージのローカライズできる文字列を定義する XML を追加します。  次の XML では、en ロケールのエラー文字列を追加します。  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  C:\\package フォルダーを Visual Studio ブートストラップ ディレクトリにコピーします。  Visual Studio 2010 の場合、これは \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages ディレクトリです。  
  
## 使用例  
 パッケージ マニフェストには、エラー メッセージ、ソフトウェア ライセンス条項、Language Pack など、ロケール固有の情報が含まれます。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)