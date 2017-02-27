---
title: "&lt;PackageFiles&gt; 要素 (ブートストラップ) | Microsoft Docs"
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
  - "<PackageFiles> 要素 [ブートストラップ]"
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# &lt;PackageFiles&gt; 要素 (ブートストラップ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`PackageFiles` 要素には、`Command` 要素の結果として実行されるインストール パッケージを定義する `PackageFile` 要素が含まれます。  
  
## 構文  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## 要素と属性  
 `PackageFiles` 要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`CopyAllPackageFiles`|省略可能です。  `false` に設定した場合、`Command` 要素から参照されているファイルだけがインストーラーによってダウンロードされます。  `true` に設定した場合、すべてのファイルがダウンロードされます。<br /><br /> `IfNotHomesite` に設定した場合で、かつ、`ComponentsLocation` を `HomeSite` に設定した場合、インストーラーは `False` に設定されたものとして動作します。それ以外の場合は、`True` と同じ動作になります。  この設定を使用すると、HomeSite のシナリオにおいて、それ自体がブートストラップであるパッケージに独自の動作を実行させることができます。<br /><br /> 既定値は `true` です。|  
  
## PackageFile  
 `PackageFile` 要素は、`PackageFiles` 要素に必須の子です。  1 つの `PackageFiles` 要素には、少なくとも 1 つの `PackageFile` 要素が必要です。  
  
 `PackageFile` には、以下の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Name`|必ず指定します。  パッケージ ファイルの名前です。  この名前は、パッケージをインストールするための条件を定義する場合に、`Command` 要素が参照する名前です。  この値は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] などのツールがパッケージを記述するために使用するローカライズされた名前を取得するために、`Strings` テーブルを検索するためのキーとしても使用されます。|  
|`HomeSite`|省略可能です。  インストーラーに含まれていない場合の、パッケージのリモート サーバー上の場所です。|  
|`CopyOnBuild`|省略可能です。  ビルド時にブートストラップがパッケージ ファイルをディスクにコピーするかどうかを指定します。  既定値は true です。|  
|`PublicKey`|パッケージ証明書の署名者の暗号化された公開キーです。  `HomeSite` を使用する場合は必ず指定します。その他の場合は、省略可能です。|  
|`Hash`|省略可能です。  パッケージ ファイルの SHA1 ハッシュです。  インストール時にファイルの整合性を検証するために使用されます。  パッケージ ファイルから同一のハッシュを計算できなかった場合、パッケージはインストールされません。|  
  
## 使用例  
 次のコード例では、Windows インストーラーなど、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 再頒布可能パッケージとその依存ファイル用のパッケージを定義しています。  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## 参照  
 [\<Product\> 要素](../deployment/product-element-bootstrapper.md)   
 [\<Package\> 要素](../deployment/package-element-bootstrapper.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)