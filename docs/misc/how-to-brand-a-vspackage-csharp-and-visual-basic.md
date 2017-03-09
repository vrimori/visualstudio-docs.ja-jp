---
title: "方法: VSPackage をブランド化する (C# および Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[バージョン情報] ダイアログ ボックス"
  - "VSPackage、スプラッシュ スクリーン"
  - "VSPackage、ブランド化"
ms.assetid: 705a41c3-63d6-4c1e-9f82-771be9191579
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 方法: VSPackage をブランド化する (C# および Visual Basic)
\[出力\] ダイアログ ボックス ENT0ENTスプラッシュ スクリーンに表示するにはVSPackage は <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> のインターフェイスを実装する必要があります。  これは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] に次の情報を指定します :  
  
-   名前  
  
-   シリアルまたはバージョン番号などID  
  
-   情報  
  
-   ロゴのアイコン  
  
 次のコードは [VSSDK のサンプル](../misc/vssdk-samples.md) になります。  
  
### IVsInstalledProduct のインターフェイスを実装するには  
  
1.  VSPackage を実装するクラスに <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> の属性を追加します。  このクラスは <xref:Microsoft.VisualStudio.Shell.Package> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> 両方から派生する必要があります。  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_1.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_1.vb)]  
  
     最初の引数はInstalledProducts のレジストリ キーの代わりに <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> の属性の <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute.UseInterface%2A>[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> を製品情報を表示するように指定します。  残りの引数は製品名と ID詳細を表示する文字列リソースをそれぞれ選択します。  ただし最初の引数が `true` であるため残りの引数は `null` です。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> を右クリックし **インターフェイスの実装**  をポイントし\[ENT1ENT\] をクリックします。  
  
3.  次のコードを使用して実装 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>。  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_2.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_2.vb)]  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はVSPackage を決め付けるに関する情報を取得するためにメソッドを呼び出します。  GetResourceString のメソッドがこの情報をローカライズするために使用されます。  
  
    > [!NOTE]
    >  コードのコメントは簡略化のため削除されます。  [VSSDK のサンプル](../misc/vssdk-samples.md) で検索できます。  
  
### 製品情報文字列を保持します。  
  
1.  VSPackage に関連付けられた .resx リソース ファイルをダブルをクリックします。  
  
     リソース エディターが開きます。  
  
2.  製品名情報と ID を選択または追加します。  
  
     次のリソース文字列に [VSSDK のサンプル](../misc/vssdk-samples.md) になります。  
  
     @101  
     正称 \(C\#\) のパッケージのスプラッシュ スクリーンと役立ちます。  
  
     @102  
     このパッケージはスプラッシュ スクリーンとヘルプのテキストとイメージとして表示する方法を示します。  
  
     @104  
     8.0  
  
3.  必要な場合はこの情報を選択および編集します。  
  
### 製品のアイコンビットマップを保存します。  
  
1.  プロジェクト リソースとしてプロジェクトにビットマップおよびアイコンを追加します。  
  
     詳細については、「[NOT IN BUILD: Adding and Editing Resources \(Visual C\#\)](http://msdn.microsoft.com/ja-jp/95f15d03-bed0-410c-8d1f-dece5199ba1e)」を参照してください。  
  
2.  リソース エディターを閉じXML またはテキスト エディターで .resx ファイルを再開します。  
  
    > [!NOTE]
    >  リソース エディターは文字列以外の項目にリソースの ID を割り当てることはできません。  
  
3.  検索するかアイコンを追加し.resx ファイルにリソースをビットマップします。  次のリソースには[VSSDK のサンプル](../misc/vssdk-samples.md) になります。  
  
    ```  
    <data name="300" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.bmp;System.Drawing.Bitmap, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    <data name="400" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.ico;System.Drawing.Icon, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    ```  
  
### ダイアログ ボックスでスプラッシュ スクリーンをテストするには  
  
-   VSPackage をテストするには[方法: バージョン情報とスプラッシュ スクリーンをテストする](../misc/how-to-test-the-help-about-and-splash-screens.md) を参照してください。  
  
## 参照  
 [VSPackage のブランド化](/visual-cpp/misc/vspackage-branding)