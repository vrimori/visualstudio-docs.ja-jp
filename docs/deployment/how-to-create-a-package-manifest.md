---
title: '方法: パッケージ マニフェストを作成する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54c2e6a231ce597e2ec6a3e04cf74521b6c10d2e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-package-manifest"></a>方法: パッケージ マニフェストを作成する
アプリケーションの前提条件を展開するには、ブートス トラップ パッケージを使用できます。 ブートス トラップ パッケージには、ロケールごとに、パッケージ マニフェストが 1 つの製品マニフェスト ファイルが含まれています。 別のローカライズされたバージョン間で共有機能は、製品マニフェストに変わります必要があります。  
  
 パッケージ マニフェストの詳細については、次を参照してください。[する方法: 製品マニフェストを作成](../deployment/how-to-create-a-product-manifest.md)です。  
  
## <a name="creating-the-package-manifest"></a>パッケージ マニフェストの作成  
  
#### <a name="to-create-the-package-manifest"></a>パッケージ マニフェストを作成するには  
  
1.  ブートス トラップ パッケージのディレクトリを作成します。 この例では、C:\package を使用します。  
  
2.  英語など、ロケールの名前を持つサブディレクトリを作成します。  
  
3.  Visual Studio で、という XML ファイルを作成する`package.xml`、C:\package\en フォルダーに保存します。  
  
4.  ブートス トラップ パッケージの名前、このローカライズされたパッケージ マニフェスト、および省略可能なライセンス契約のカルチャを列挙する XML を追加します。 次の XML は、変数を使用して`DisplayName`と`Culture`、以降の要素で定義されています。  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  ロケール固有のディレクトリ内にあるすべてのファイルを列挙する XML を追加します。 次の XML に適用できる eula.txt というファイルを使用して、 **en**ロケール。  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  ブートス トラップ パッケージのローカライズ可能な文字列を定義する XML を追加します。 次の XML では、en ロケールのエラー文字列を追加します。  
  
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
  
7.  C:\package フォルダーを Visual Studio ブートス トラップ ディレクトリにコピーします。 Visual Studio 2010 の場合、これは、\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages ディレクトリです。  
  
## <a name="example"></a>例  
 パッケージ マニフェストには、エラー メッセージ、ソフトウェア ライセンス条項、および言語パックなど、ロケールに固有の情報が含まれています。  
  
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
  
## <a name="see-also"></a>関連項目  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)