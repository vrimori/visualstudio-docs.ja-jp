---
title: '方法: ローカライズされたブートス トラップ パッケージを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1083633410c42c63f8c3e9a2ff341a2278f0b63a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153216"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>方法: ローカライズされたブートス トラップ パッケージを作成します。
ブートス トラップ パッケージを作成した後は、ロケールごとに 2 つ以上のファイルを作成してブートス トラップ パッケージのローカライズ版を作成できますソフトウェア ライセンス条項ファイル (など、 *eula.rtf*) とパッケージ マニフェスト (*。package.xml*)。  
  
 既定では、Visual Studio 2010 には .NET Framework 4、.NET Framework 4 Client Profile、F# Runtime 2.0、および F# Runtime 4.0 用のローカライズ版のブートストラップ パッケージのみが用意されています。 3 つのステップを実行することにより、その他のブートストラップのローカライズ版パッケージを作成できます。  
  
1.  ロケール名に続くという名前のフォルダーを作成する*\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >* します。  
  
2.  ブートストラップ パッケージのソフトウェア ライセンス条項を示すファイルを作成し、新しいフォルダーに格納します。  
  
3.  という名前のパッケージ マニフェストを作成する*package.xml*文字列とカルチャを更新し、新しいフォルダーにファイルを配置します。 Visual Studio のブートス トラップは、対象言語で既に作成した場合に、Visual Studio をコピーすることができます*package.xml*ファイルし、この手順で変更します。  
  
> [!NOTE]
>  変更することで、アプリケーションをローカライズするにはアプリケーションを展開するセットアップ プロジェクトを使用する場合、**ローカリゼーション**プロパティ。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>ローカライズ版のブートストラップ パッケージを作成するには  
  
1.  ロケール名に基づいた名前のフォルダーを作成します。  
  
     32 ビットのコンピューターでのフォルダーを作成、 *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\* フォルダー。  
  
     64 ビットのコンピューターでのフォルダーを作成、 *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\* フォルダー。  
  
     次の表は、ロケールに合わせるために使用できるフォルダー名を示します。  
  
    |ロケール|フォルダー名|  
    |------------|-----------------|  
    |簡体字中国語|zh-Hans|  
    |繁体字中国語|zh-Hant|  
    |チェコ語|cs|  
    |ドイツ語|de|  
    |英語|en|  
    |スペイン語|es|  
    |フランス語|fr|  
    |イタリア語|it|  
    |韓国語|ko|  
    |日本語|ja|  
    |ポーランド語|pl|  
    |ポルトガル語 (ブラジル)|pt-BR|  
    |ロシア語|ru|  
    |トルコ語|tr|  
  
2.  ブートストラップ パッケージのソフトウェア ライセンス条項を示すファイルを作成し、新しいフォルダーに格納します。  
  
3.  という名前のパッケージ マニフェストを作成する*package.xml*され、新しいフォルダーに配置されます。 詳細については、次を参照してください。[方法: パッケージ マニフェストを作成する](../deployment/how-to-create-a-package-manifest.md)します。  
  
4.  パッケージ マニフェストの `<Strings>` セクションを更新して、文字列がロケールに対応する正しい言語で表示されるようにします。  
  
5.  `<String Name="Culture">` の値をフォルダー名と一致するように変更します。  
  
6.  保存、 *package.xml*ファイル。  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>フランス語でローカライズした .NET Framework 3.5 Service Pack 1 用のブートストラップ パッケージを作成するには  
  
1.  という名前のフォルダーを作成する*fr*します。 フォルダー名はロケール名と一致する必要があります。  
  
     32 ビットのコンピューターでのフォルダーを作成、 *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\* フォルダー。  
  
     64 ビットのコンピューターでのフォルダーを作成、 *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\* フォルダー。  
  
2.  ローカライズされたバージョンに、ソフトウェア ライセンス条項の配置、 *fr*フォルダー。  
  
3.  コピー、 *\Program Files (x86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml*ファイルを*fr*フォルダー、および XML デザイナーでファイルを開きます。  
  
4.  パッケージ マニフェストの `<Strings>` セクションを更新して、エラー文字列がフランス語で表示されるようにします。  
  
5.  変更、`<String Name="Culture">`値を*fr*します。  
  
6.  保存、 *package.xml*ファイル。  
  
## <a name="see-also"></a>関連項目  
 [ブートス トラップ パッケージを作成します。](../deployment/creating-bootstrapper-packages.md)   
 [アプリケーション展開の前提条件](../deployment/application-deployment-prerequisites.md)   
 [方法: パッケージ マニフェストを作成する](../deployment/how-to-create-a-package-manifest.md)