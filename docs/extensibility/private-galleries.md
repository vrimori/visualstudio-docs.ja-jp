---
title: "プライベート ギャラリー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プライベート VSIX ギャラリー"
  - "VSIX の非公開のギャラリー"
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# プライベート ギャラリー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コントロール、テンプレート、およびに送信することによって開発ツールを共有することができます、 *プライベート ギャラリー* 次のように、組織のイントラネット上。  
  
-   Atom \(RSS\) フィード、イントラネット上に適切に構成されている中央の場所 \(リポジトリ\) を作成します。 詳細については、「[方法: Atom を作成するプライベート ギャラリーのフィード](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)」を参照してください。  
  
-   プライベート ギャラリーを記述する .pkgdef ファイルを配布します。 管理者はプライベート ギャラリーを同時に多数のコンピューターに接続するときにこの構成をお勧めします。  
  
## 拡張機能と Visual Studio での更新プログラムへのプライベート ギャラリーの追加  
 非公開のギャラリーが利用できる場合に追加できる **拡張機能と更新プログラム** Visual Studio でします。  
  
 ![拡張機能マネージャーの追加ダイアログ](~/extensibility/media/em_adddialog.png "EM\_AddDialog")  
  
#### 拡張機能と更新プログラムにプライベート ギャラリーを追加するには  
  
1.  メニュー バーの **\[ツール\]**、**\[オプション\]** の順にクリックします。  
  
2.  **環境** ノードで、選択 **拡張機能と更新プログラム**します。  
  
3.  **\[追加\]** ボタンをクリックします。  
  
4.  **名** フィールドで、たとえば、プライベート ギャラリーの名前を入力 `My Gallery`します。  
  
5.  **URL** フィールドに、Atom フィードまたはプライベート ギャラリーをホストしている SharePoint サイトの URL を入力します。  
  
    1.  プライベート ギャラリーに接続するホストが Atom フィードである場合は、このいずれかの URL のようになります: http:\/\/www.mywebsite\/mygallery\/atom.xml です。  この URL は、ファイルまたはネットワーク パスを参照できます。  
  
    2.  ホストが、SharePoint サイトの場合、URL のようになりますこのいずれか: http:\/\/mysharepoint\/sites\/mygallery\/forms\/AllItems.aspx です。  
  
### プライベート ギャラリーの管理  
 行うことができますプライベート ギャラリー利用可能な複数のコンピューターに同時に各コンピューター上のシステム レジストリを変更することで。 これを実現するには、新しいレジストリ キーとその値を記述した .pkgdef ファイルを作成します。  このファイルの形式は次のとおりです。  
  
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
  
 詳細については、「[方法: レジストリ設定を使用してプライベート ギャラリーを管理](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)」を参照してください。  
  
## プライベート ギャラリーから拡張機能をインストールします。  
 検索してプライベート ギャラリーに Visual Studio 拡張機能をインストール **拡張機能と更新プログラム**します。 次の手順は、という名前のプライベート ギャラリーを使用して `My Gallery`します。  
  
 ![プライベート ギャラリーをインストールする拡張機能マネージャー](~/extensibility/media/em_.png "EM\_")  
  
#### 検索してプライベート ギャラリーから拡張機能をインストールするには  
  
1.  メニュー バーで、**\[ツール\]**、**\[拡張機能と更新プログラム\]** の順にクリックします。  
  
2.  左側のウィンドウで \[ **オンラインの拡張機能**, 、し、\[ **マイ ギャラリー**します。  
  
3.  右側のウィンドウで、拡張機能を選択し、選択、 **ダウンロード** \] ボタンをクリックします。  
  
## プライベート ギャラリーから拡張機能を更新  
 プライベート ギャラリーには、新しいバージョンの Visual Studio 拡張機能が追加された、インストールされている拡張機能を更新できます。 次の手順は、という名前のプライベート ギャラリーを使用して `My Repository`します。  
  
 ![拡張機能マネージャーのプライベート ギャラリーの更新](~/extensibility/media/em_update.png "EM\_Update")  
  
#### 非公開のギャラリーからインストールされている拡張機能を更新するには  
  
1.  メニュー バーで、**\[ツール\]**、**\[拡張機能と更新プログラム\]** の順にクリックします。  
  
2.  左側のウィンドウで \[ **更新**, 、し、\[ **マイ リポジトリ**します。  
  
3.  右側のウィンドウで、拡張機能を選択し、選択、 **更新** \] ボタンをクリックします。  
  
## 参照  
 [Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)   
 [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)