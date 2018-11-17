---
title: プライベート ギャラリー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 910764df2f6a6e3069136bce64b77f267e473b9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749957"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コントロール、テンプレート、および投稿することで開発したツールを共有することができます、*プライベート ギャラリー*次のように、組織のイントラネット上。  
  
-   イントラネット上で適切に構成されている中央の場所 (リポジトリ) にフィード Atom (RSS) を作成します。 詳細については、次を参照してください。[方法: プライベート ギャラリーの Atom フィードを作成する](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)します。  
  
-   プライベート ギャラリーを記述する .pkgdef ファイルを配布します。 プライベート ギャラリーを同時に多くのコンピューターに接続する管理者のためには、この構成をお勧めします。  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>拡張機能と Visual Studio での更新プログラムへのプライベート ギャラリーの追加  
 プライベート ギャラリーが利用できる場合を追加**拡張機能と更新**Visual Studio でします。  
  
 ![[追加] ダイアログの拡張機能マネージャー](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>拡張機能と更新プログラムにプライベート ギャラリーを追加するには  
  
1.  メニュー バーの **[ツール]**、 **[オプション]** の順にクリックします。  
  
2.  **環境**ノードの **拡張機能と更新**します。  
  
3.  **[追加]** ボタンをクリックします。  
  
4.  **名前**フィールドに、たとえば、プライベート ギャラリーの名前を入力`My Gallery`します。  
  
5.  **URL**フィールドに、Atom フィードまたはプライベート ギャラリーをホストしている SharePoint サイトの URL を入力します。  
  
    1.  プライベート ギャラリーに接続するホストが Atom フィードの場合は、このいずれかの URL のようになります: http://www.mywebsite/mygallery/atom.xml します。  この URL は、ファイルまたはネットワーク パスを参照できます。  
  
    2.  ホストが SharePoint サイトの場合は、URL のようになりますこのいずれか:http://mysharepoint/sites/mygallery/forms/AllItems.aspxします。  
  
### <a name="managing-private-galleries"></a>プライベート ギャラリーを管理します。  
 行うことができますをプライベート ギャラリー使用可能な複数のコンピューターに同時に各コンピューター上のシステム レジストリを変更することで。 これを実現するには、新しいレジストリ キーとその値を記述する .pkgdef ファイルを作成します。  このファイルの形式は次のとおりです。  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 詳細については、次を参照してください。[方法: をプライベート ギャラリーで設定を使用してレジストリを管理](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)します。  
  
## <a name="installing-extensions-from-a-private-gallery"></a>プライベート ギャラリーから拡張機能のインストール  
 検索してプライベート ギャラリーから Visual Studio 拡張機能をインストールできます**拡張機能と更新**します。 次の手順を使用して、という名前のプライベート ギャラリー`My Gallery`します。  
  
 ![プライベート ギャラリーをインストールする拡張機能マネージャー](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>検索してプライベート ギャラリーから拡張機能をインストールするには  
  
1.  メニュー バーで、**[ツール]**、**[拡張機能と更新プログラム]** の順にクリックします。  
  
2.  左側のウィンドウで次のように選択します。**拡張機能のオンライン**、し、**マイ ギャラリー**します。  
  
3.  右側のウィンドウで、拡張機能を選択し、選択、**ダウンロード**ボタンをクリックします。  
  
## <a name="updating-extensions-from-a-private-gallery"></a>プライベート ギャラリーから拡張機能の更新  
 プライベート ギャラリーでは、Visual Studio 拡張機能の新しいバージョンがポストされた、インストールされている拡張機能を更新することができます。 次の手順を使用して、という名前のプライベート ギャラリー`My Repository`します。  
  
 ![拡張機能マネージャーのプライベート ギャラリーの更新](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>プライベート ギャラリーからインストールされている拡張機能を更新するには  
  
1.  メニュー バーで、**[ツール]**、**[拡張機能と更新プログラム]** の順にクリックします。  
  
2.  左側のウィンドウで次のように選択します。**更新**、し、**マイ リポジトリ**します。  
  
3.  右側のウィンドウで、拡張機能を選択し、選択、 **Update**ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [検索と Visual Studio 拡張機能の使用](../ide/finding-and-using-visual-studio-extensions.md)   
 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)

