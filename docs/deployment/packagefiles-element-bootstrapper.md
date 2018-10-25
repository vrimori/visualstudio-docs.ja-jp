---
title: '&lt;PackageFiles&gt;要素 (ブートス トラップ) |Microsoft Docs'
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
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84451a90e316a98a9998e1a64e68a72668bd4781
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813766"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles&gt;要素 (ブートス トラップ)
`PackageFiles`要素が含まれます`PackageFile`の結果として実行されるインストール パッケージを定義するには、要素、`Command`要素。  

## <a name="syntax"></a>構文  

```xml  
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

## <a name="elements-and-attributes"></a>要素と属性  
 `PackageFiles` 要素には、次の属性があります。  

|属性|説明|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|任意。 場合設定`false`、インストーラーから参照されるファイルをダウンロードのみが、`Command`要素。 場合設定`true`、すべてのファイルがダウンロードされます。<br /><br /> 場合に設定`IfNotHomesite`、インストーラーには、同じ動作がまるで`False`場合`ComponentsLocation`に設定されている`HomeSite`、し、それ以外の場合は動作が同じ場合と`True`。 この設定をそれ自体がパッケージに HomeSite シナリオでは、独自の動作を実行するブートス トラップを許可することができます。<br /><br /> 既定値は `true` です。|  

## <a name="packagefile"></a>PackageFile  
 `PackageFile`要素の子である、`PackageFiles`要素。 A`PackageFiles`要素が少なくとも 1 つあります`PackageFile`要素。  

 `PackageFile` 次の属性があります。  


| 属性 | 説明 |
|---------------| - |
| `Name` | 必須。 パッケージ ファイルの名前。 これは、名前を`Command`パッケージをインストールするための条件を定義する場合に、要素を参照します。 この値はへのキーとしても使用、`Strings`などのツールをローカライズされた名前を取得するテーブル[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]が使用して、パッケージを記述します。 |
| `HomeSite` | 任意。 インストーラーに含まれてない場合は、リモート サーバー上のパッケージの場所。 |
| `CopyOnBuild` | 任意。 ブートス トラップがビルド時に、ディスク上にパッケージ ファイルをコピーする必要があるかどうかを指定します。 既定値は true です。 |
| `PublicKey` | パッケージの証明書の署名者の公開暗号化キー。 場合に、必ず`HomeSite`は使用しない場合は省略可能です。 |
| `Hash` | 任意。 パッケージ ファイルの SHA1 ハッシュ。 これは、インストール時に、ファイルの整合性を検証に使用されます。 パッケージ ファイルからは、同一のハッシュを計算することはできません、パッケージはインストールされていません。 |

## <a name="example"></a>例  
 次のコード例は、のパッケージを定義、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]再頒布可能パッケージとその依存関係、Windows インストーラーなど。  

```xml  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  

## <a name="see-also"></a>関連項目  
 [\<製品 > 要素](../deployment/product-element-bootstrapper.md)   
 [\<パッケージ > 要素](../deployment/package-element-bootstrapper.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)