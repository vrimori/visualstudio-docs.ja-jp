---
title: '方法: パッケージ マニフェストを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2941000e9fa2c6f1d9fd4835c9fd0b8fa1fd1b4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182430"
---
# <a name="how-to-create-a-package-manifest"></a>方法: パッケージ マニフェストを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリケーションの必須コンポーネントを展開するには、ブートス トラップ パッケージを使用できます。 ブートス トラップ パッケージには、ロケールごとに、パッケージ マニフェストが 1 つの製品マニフェスト ファイルが含まれています。 別のローカライズされたバージョン間で共有機能は、製品マニフェストに移動してください。  
  
 パッケージ マニフェストの詳細については、次を参照してください。[方法: Create a Product Manifest](../deployment/how-to-create-a-product-manifest.md)します。  
  
## <a name="creating-the-package-manifest"></a>パッケージ マニフェストの作成  
  
#### <a name="to-create-the-package-manifest"></a>パッケージ マニフェストを作成するには  
  
1.  ブートス トラップ パッケージ用のディレクトリを作成します。 この例では、C:\package を使用します。  
  
2.  英語など、ロケールの名前を持つサブディレクトリを作成します。  
  
3.  Visual Studio では、という XML ファイルを作成`package.xml`、C:\package\en フォルダーに保存します。  
  
4.  このローカライズされたパッケージ マニフェストと省略可能なライセンス契約のカルチャにブートス トラップ パッケージの名前を一覧表示する XML を追加します。 次の XML は、変数を使用して`DisplayName`と`Culture`、以降の要素で定義されています。  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  ロケール固有のディレクトリ内にあるすべてのファイルを一覧表示の XML を追加します。 次の XML に適用できる eula.txt がという名前のファイルを使用して、 **en**ロケール。  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  ブートス トラップ パッケージのローカライズ可能な文字列を定義する XML を追加します。 次の XML は、英語ロケールのエラー文字列を追加します。  
  
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
  
7.  C:\package フォルダーを Visual Studio ブートス トラップ ディレクトリにコピーします。 Visual Studio 2010 では、これは、\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages ディレクトリです。  
  
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



