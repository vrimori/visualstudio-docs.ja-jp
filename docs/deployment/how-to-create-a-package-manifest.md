---
title: '方法: パッケージ マニフェストを作成する |Microsoft Docs'
ms.date: 11/04/2016
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
ms.openlocfilehash: a1f965bdbd19193bfaa942d5f3635b0652f0e9c4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943474"
---
# <a name="how-to-create-a-package-manifest"></a>方法: パッケージ マニフェストを作成する
アプリケーションの必須コンポーネントを展開するには、ブートス トラップ パッケージを使用できます。 ブートス トラップ パッケージには、ロケールごとに、パッケージ マニフェストが 1 つの製品マニフェスト ファイルが含まれています。 別のローカライズされたバージョン間で共有機能は、製品マニフェストに移動してください。  
  
 パッケージ マニフェストの詳細については、次を参照してください。[方法。製品マニフェストを作成する](../deployment/how-to-create-a-product-manifest.md)  
  
## <a name="create-the-package-manifest"></a>パッケージ マニフェストを作成します。  
  
#### <a name="to-create-the-package-manifest"></a>パッケージ マニフェストを作成するには  
  
1.  ブートス トラップ パッケージ用のディレクトリを作成します。 この例では*C:\package*します。  
  
2.  など、ロケールの名前を持つサブディレクトリを作成*en*英語の場合。  
  
3.  Visual Studio では、という XML ファイルを作成*package.xml*、保存して、 *C:\package\en*フォルダー。  
  
4.  このローカライズされたパッケージ マニフェストと省略可能なライセンス契約のカルチャにブートス トラップ パッケージの名前を一覧表示する XML を追加します。 次の XML は、変数を使用して`DisplayName`と`Culture`、以降の要素で定義されています。  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  ロケール固有のディレクトリ内にあるすべてのファイルを一覧表示の XML を追加します。 次の XML という名前のファイルを使用して*eula.txt*に適用される、 **en**ロケール。  
  
    ```xml  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  ブートス トラップ パッケージのローカライズ可能な文字列を定義する XML を追加します。 次の XML に追加のエラー文字列、 **en**ロケール。  
  
    ```xml  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  コピー、 *C:\package*を Visual Studio ブートス トラップ ディレクトリのフォルダー。 これは Visual Studio 2010 の場合、 *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*ディレクトリ。  
  
## <a name="example"></a>例  
 パッケージ マニフェストには、エラー メッセージ、ソフトウェア ライセンス条項、および言語パックなど、ロケールに固有の情報が含まれています。  
  
```xml  
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