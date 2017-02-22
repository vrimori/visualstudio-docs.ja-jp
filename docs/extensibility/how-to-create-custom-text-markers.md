---
title: "方法: カスタム テキスト マーカーを作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシのカスタム テキスト マーカー"
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: カスタム テキスト マーカーを作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

強調したりコードを整理したりするカスタム テキスト マーカーを作成する場合は、以下の手順を実行する必要があります。  
  
-   その他のツールがアクセスできるように、新しいテキスト マーカーを登録します。  
  
-   既定の実装とテキストのマーカーの構成を提供します。  
  
-   させるその他のプロセスで使用できるサービスを作成するテキストのマーカーの使用  
  
 コードの領域にテキスト マーカーを適用する方法の詳細については、次を参照してください。 [方法: テキストのマーカーを使用して](../extensibility/how-to-use-text-markers.md)します。  
  
### <a name="to-register-a-custom-marker"></a>カスタム マーカーを登録するには  
  
1.  レジストリ エントリを作成します。  
  
     Hkey_local_machine \software\microsoft\visualstudio\\*\< バージョン>*\Text Editor\External マーカー\\*\< MarkerGUID>*  
  
     *\< MarkerGUID>*は、 `GUID` 追加される、マーカーを識別するために使用  
  
     *\< バージョン>* のバージョンは、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 、たとえば 8.0  
  
     *\< PackageGUID>* オートメーション オブジェクトを実装する VSPackage の guid を指定します。  
  
    > [!NOTE]
    >  Hkey_local_machine \software\microsoft\visualstudio のルート パス\\*\< バージョン>* 詳細については、「Visual Studio シェルの初期化時に代替ルートでオーバーライドできる [コマンド ライン スイッチ](../extensibility/command-line-switches-visual-studio-sdk.md)します。  
  
2.  Hkey_local_machine \software\microsoft\visualstudio 下にある 4 つの値を作成する\\*\< バージョン>*\Text Editor\External マーカー\\*\< MarkerGUID>*  
  
    -   (既定)  
  
    -   サービス  
  
    -   DisplayName  
  
    -   パッケージ  
  
    -   `Default` REG_SZ 型の省略可能なエントリです。 設定すると、エントリの値は、有用な識別情報、たとえば「カスタム テキスト マーカー」を含む文字列です。  
  
    -   `Service` REG_SZ 型のエントリは proffering してカスタム テキスト マーカーを提供するサービスの GUID 文字列を含む <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>します。 形式は、{XXXXXX XXXX XXXX XXXX XXXXXXXXX} です。  
  
    -   `DisplayName` カスタム テキスト マーカーの名前のリソース ID を含む REG_SZ 型のエントリです。 形式は、#YYYY です。  
  
    -   `Package` エントリの種類 REG_SZ を含んでいるは、 `GUID` VSPackage サービスを提供するは、サービスの下に一覧表示します。 形式は、{XXXXXX XXXX XXXX XXXX XXXXXXXXX} です。  
  
### <a name="to-create-a-custom-text-marker"></a>カスタム テキスト マーカーを作成するには  
  
1.  実装、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> インターフェイスです。  
  
     このインターフェイスの実装では、動作と、カスタムのマーカーの種類の外観を定義します。  
  
     このインターフェイスが呼び出されます  
  
    1.  ユーザーは、最初に、IDE を起動します。  
  
    2.  ユーザーが選択、 **既定値をリセット** ボタン、 **フォントおよび色** ] プロパティ ページで、 **環境** の左側のウィンドウにあるフォルダー、 **オプション** から取得した] ダイアログ ボックス、 **ツール** IDE のメニュー。  
  
2.  実装、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> メソッドを指定する `IVsPackageDefinedTextMarkerType` 実装する必要がありますに基づいて返されるマーカーの種類のメソッド呼び出しで指定された GUID です。  
  
     環境では、このメソッドの最初の時間、カスタムのマーカーの種類が作成され、カスタムのマーカーの種類を識別する GUID を指定を呼び出します。  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>マーカーの種類をサービスとして提供するには  
  
1.  呼び出す、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> 方法 <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>します。  
  
     ポインター <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> が返されます。  
  
2.  呼び出す、 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> GUID、カスタム マーカーの種類のサービスを識別するの実装へのポインターを提供することを指定して、メソッド、 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> インターフェイスです。  <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 実装の実装にポインターを返す必要があります <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> インターフェイスです。  
  
     サービスが返されることを識別する一意のクッキー。 呼び出すことによって、カスタム マーカーの種類のサービスを取り消すこの cookie を使用した後で、 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> のメソッド、 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> この cookie の値を指定するインターフェイスです。  
  
## <a name="see-also"></a>参照  
 [レガシ API でテキストのマーカーの使用](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [方法: 標準のテキストのマーカーを追加](../extensibility/how-to-add-standard-text-markers.md)   
 [方法: エラー マーカーを実装します。](../extensibility/how-to-implement-error-markers.md)   
 [方法: テキストのマーカーを使用します。](../extensibility/how-to-use-text-markers.md)