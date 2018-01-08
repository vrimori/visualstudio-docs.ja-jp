---
title: "方法: カスタム テキスト マーカーを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d30ad5b61f59e6183067ddcc789b2fc796c7aef9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-custom-text-markers"></a>方法: カスタム テキスト マーカーを作成します。
カスタム テキストを強調したり、コードの整理にマーカーを作成する場合は、以下の手順を実行する必要があります。  
  
-   その他のツールがアクセスできるように、新しいテキスト マーカーを登録します。  
  
-   既定の実装とテキスト マーカーの構成を提供します。  
  
-   他のプロセスが使用できるようにサービスを作成するテキスト マーカーの使用  
  
 コード領域にテキスト マーカーを適用する方法の詳細については、次を参照してください。[する方法: を使用してテキスト マーカー](../extensibility/how-to-use-text-markers.md)です。  
  
### <a name="to-register-a-custom-marker"></a>カスタム マーカーを登録するには  
  
1.  次のようにレジストリ エントリを作成します。  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<バージョン >*\Text Editor\External マーカー\\*\<MarkerGUID >*  
  
     *\<MarkerGUID >*は、`GUID`追加される、マーカーを識別するために使用  
  
     *\<バージョン >*のバージョンは、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]8.0 などの  
  
     *\<PackageGUID >*オートメーション オブジェクトを実装する VSPackage の GUID です。  
  
    > [!NOTE]
    >  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio のルート パス\\*\<バージョン >*詳細については、「Visual Studio シェルが初期化される場合、代替ルートで上書きすることができます[コマンド ライン スイッチ](../extensibility/command-line-switches-visual-studio-sdk.md)です。  
  
2.  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio 下にある 4 つの値を作成する\\*\<バージョン >*\Text Editor\External マーカー\\*\<MarkerGUID>*  
  
    -   (既定)  
  
    -   サービス  
  
    -   DisplayName  
  
    -   Package  
  
    -   `Default`種類 REG_SZ の省略可能なエントリです。 設定すると、エントリの値は、有用な識別情報、たとえば「カスタム テキスト マーカー」を含む文字列です。  
  
    -   `Service`種類 REG_SZ のエントリが含まれている proffering によって、カスタム テキスト マーカーを提供するサービスの GUID 文字列<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>です。 形式は、{XXXXXX XXXX XXXX XXXX XXXXXXXXX} です。  
  
    -   `DisplayName`カスタム テキスト マーカーの名前のリソース ID を種類 REG_SZ のエントリを含むです。 形式は、#YYYY です。  
  
    -   `Package`REG_SZ が含まれる型のエントリ、`GUID`サービスを提供する VSPackage のサービスの下で一覧表示します。 形式は、{XXXXXX XXXX XXXX XXXX XXXXXXXXX} です。  
  
### <a name="to-create-a-custom-text-marker"></a>カスタム テキスト マーカーを作成するには  
  
1.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> インターフェイスを実装します。  
  
     このインターフェイスの実装では、動作と、カスタムのマーカーの種類の外観を定義します。  
  
     このインターフェイスが呼び出されます  
  
    1.  ユーザーは、最初に、IDE を開始します。  
  
    2.  ユーザーが選択、**リセット**下にあるボタンをクリックして、**フォントおよび色**プロパティ ページで、**環境**の左側のウィンドウにあるフォルダー、 **オプション** ダイアログ ボックスがから取得した、**ツール**IDE のメニュー。  
  
2.  実装、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A>メソッドを指定する`IVsPackageDefinedTextMarkerType`実装する必要がありますに基づいて返されるマーカーの種類、メソッドの呼び出しで指定された GUID。  
  
     環境では、このメソッドの最初の時間、カスタムのマーカーの種類が作成され、カスタムのマーカーの種類を識別する GUID を指定を呼び出します。  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>サービスとして、マーカーの種類を proffer に  
  
1.  呼び出す、<xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A>メソッド<xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>です。  
  
     ポインター<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>が返されます。  
  
2.  呼び出す、 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> 、カスタム マーカーの種類のサービスを識別およびの実装へのポインターを提供する GUID を指定して、メソッド、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>インターフェイスです。 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>実装の実装にポインターを返す必要があります<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>インターフェイスです。  
  
     サービスが返されることを識別する一意の cookie。 後を呼び出すことによって、カスタム マーカーの種類のサービスを取り消すこの cookie を使用することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A>のメソッド、<xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>この cookie の値を指定するインターフェイスです。  
  
## <a name="see-also"></a>参照  
 [レガシ API でテキスト マーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキストのマーカーの追加](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: エラー マーカーを実装します。](../extensibility/how-to-implement-error-markers.md)   
 [方法: テキスト マーカーを使用](../extensibility/how-to-use-text-markers.md)