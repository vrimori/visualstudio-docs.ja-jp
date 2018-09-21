---
title: 相互運用機能アセンブリ コマンド ハンドラーの登録 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: da8c70517fe8d8ce08f886e70f5dea9827739f55
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495831"
---
# <a name="registering-interop-assembly-command-handlers"></a>相互運用機能アセンブリ コマンド ハンドラーの登録
VSPackage に登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) は、そのコマンドを正しくルーティングされるようにします。  
  
 手動で編集するか、Registrar (.rgs) ファイルを使用して、レジストリを更新できます。 詳細については、次を参照してください。 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)します。  
  
 管理パッケージ フレームワーク (MPF) は、この機能によって、<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>クラス。  
  
 [コマンドの表形式のリファレンス](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f)アンマネージ サテライト dll の UI ではリソースがあります。  
  
## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage のコマンド ハンドラーの登録  
 ユーザー インターフェイス (UI) のハンドラーとして機能する VSPackage-ベースのコマンドは、VSPackage にちなんだ名前のレジストリ エントリを必要と`GUID`します。 このレジストリ エントリには、VSPackage の UI のリソース ファイルとそのファイル内でメニュー リソースの場所を指定します。 Hkey_local_machine \software\microsoft\visualstudio の下にレジストリ エントリ自体も\\*\<バージョン >* \Menus、場所*\<バージョン >* バージョンである[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]たとえば 9.0、します。  
  
> [!NOTE]
>  Hkey_local_machine \software\microsoft\visualstudio のルート パス\\*\<バージョン >* 代替で上書きすることができる場合にルート、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]シェルが初期化されます。 ルート パスの詳細については、次を参照してください。 [Windows インストーラーで Vspackage をインストールする](../../extensibility/internals/installing-vspackages-with-windows-installer.md)します。  
  
### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU のリソースのレジストリ エントリ  
 レジストリ エントリの構造です。  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> は、 `GUID` {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX} の形式で、VSPackage の。  
  
 *\<リソース情報 >* コンマで区切られた 3 つの要素で構成されます。 これらの要素の順序では。  
  
 \<*リソース DLL へのパス*>、 \< *] メニューの [リソース ID*>、 \<*メニュー バージョン*>  
  
 次の表は、フィールドの\<*リソース情報*>。  
  
|要素|説明|  
|-------------|-----------------|  
|\<*リソース DLL へのパス*>|これは、リソース メニュー リソースを含む DLL への完全パスまたはこれが空白のまま、VSPackage のリソース DLL が使用することを示す (自体、VSPackage が登録されているパッケージのサブキーで、指定した)。<br /><br /> このフィールドを空白になります。|  
|\<*メニュー リソース ID*>|これはのリソース ID、`CTMENU`からがコンパイルされると、VSPackage のすべての UI 要素が含まれるリソースを[.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)ファイル。|  
|\<*メニューのバージョン*>|これは、バージョンとして使用する数値、`CTMENU`リソース。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 内容を再マージに必要なかどうかを決定する値を使用して、 `CTMENU` 、キャッシュのすべてを持つリソース`CTMENU`リソース。 再マージは、devenv の setup コマンドを実行することによってトリガーされます。<br /><br /> この値が 1 に設定されで変更のたびにインクリメントされます。 最初にする必要がありますする、`CTMENU`リソース、を再マージが発生する前にします。|  
  
### <a name="example"></a>例  
 リソースのエントリをいくつかの例を次に示します。  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [相互運用機能アセンブリを使用するコマンドとメニュー](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)