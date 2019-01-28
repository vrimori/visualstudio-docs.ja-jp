---
title: プライベート ギャラリー |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a764b10f295e10ab1ef4083948aa7792195ea9b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008245"
---
# <a name="private-galleries"></a>プライベート ギャラリー
コントロール、テンプレート、および投稿することで開発したツールを共有することができます、*プライベート ギャラリー*次のように、組織のイントラネット上。  
  
-   イントラネット上で適切に構成されている中央の場所 (リポジトリ) にフィード Atom (RSS) を作成します。 詳細については、「[方法 :Atom プライベート ギャラリーのフィードを作成](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)です。  
  
-   配布、 *.pkgdef*ファイルをプライベート ギャラリーについて説明します。 プライベート ギャラリーを同時に多くのコンピューターに接続する管理者のためには、この構成をお勧めします。  
  
## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>拡張機能と Visual Studio での更新プログラムにプライベート ギャラリーを追加します。  
 プライベート ギャラリーが利用できる場合を追加**拡張機能と更新**Visual Studio でします。  
  
 ![[追加] ダイアログの拡張機能マネージャー](../extensibility/media/em_adddialog.png "EM_AddDialog")  
  
### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>拡張機能と更新プログラムにプライベート ギャラリーを追加するには  
  
1.  メニュー バーの **[ツール]**  >  **[オプション]** の順にクリックします。  
  
2.  **環境**ノードの **拡張機能と更新**します。  
  
3.  **[追加]** ボタンをクリックします。  
  
4.  **名前**フィールドに、たとえば、プライベート ギャラリーの名前を入力`My Gallery`します。  
  
5.  **URL**フィールドに、Atom フィードまたはプライベート ギャラリーをホストしている SharePoint サイトの URL を入力します。  
  
    1.  プライベート ギャラリーに接続するホストが Atom フィードの場合は、このいずれかの URL のようになります: http://www.mywebsite/mygallery/atom.xml します。  この URL は、ファイルまたはネットワーク パスを参照できます。  
  
    2.  ホストが SharePoint サイトの場合は、URL のようになりますこのいずれか:http://mysharepoint/sites/mygallery/forms/AllItems.aspxします。  
  
### <a name="manage-private-galleries"></a>プライベート ギャラリーを管理します。  
 行うことができますをプライベート ギャラリー使用可能な複数のコンピューターに同時に各コンピューター上のシステム レジストリを変更することで。 これを行うには、作成、 *.pkgdef*ファイルを新しいレジストリ キーとその値について説明します。  このファイルの形式は次のとおりです。  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 詳細については、「[方法 :レジストリ設定を使用してプライベート ギャラリーを管理](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)します。  
  
## <a name="install-extensions-from-a-private-gallery"></a>プライベート ギャラリーから拡張機能をインストールします。  
 検索してプライベート ギャラリーから Visual Studio 拡張機能をインストールできます**拡張機能と更新**します。 次の手順を使用して、という名前のプライベート ギャラリー`My Gallery`します。  
  
 ![プライベート ギャラリーをインストールする拡張機能マネージャー](../extensibility/media/em_.png "EM_")  
  
### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>検索してプライベート ギャラリーから拡張機能をインストールするには  
  
1.  メニュー バーで、**ツール** > **拡張機能と更新**します。  
  
2.  左側のウィンドウで次のように選択します。**拡張機能のオンライン**、し、**マイ ギャラリー**します。  
  
3.  右側のウィンドウで、拡張機能を選択し、選択、**ダウンロード**ボタンをクリックします。  
  
## <a name="update-extensions-from-a-private-gallery"></a>プライベート ギャラリーから拡張機能を更新します。  
 プライベート ギャラリーでは、Visual Studio 拡張機能の新しいバージョンがポストされた、インストールされている拡張機能を更新することができます。 次の手順を使用して、という名前のプライベート ギャラリー`My Repository`します。  
  
 ![拡張機能マネージャーのプライベート ギャラリーの更新](../extensibility/media/em_update.png "EM_Update")  
  
### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>プライベート ギャラリーからインストールされている拡張機能を更新するには  
  
1.  メニュー バーで、**ツール** > **拡張機能と更新**します。  
  
2.  左側のウィンドウで次のように選択します。**更新**、し、**マイ リポジトリ**します。  
  
3.  右側のウィンドウで、拡張機能を選択し、選択、 **Update**ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [検索し、Visual Studio 拡張機能の使用](../ide/finding-and-using-visual-studio-extensions.md)   
 [Visual Studio 拡張機能を出荷します。](../extensibility/shipping-visual-studio-extensions.md)