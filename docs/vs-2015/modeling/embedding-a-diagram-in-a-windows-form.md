---
title: Windows フォームでのダイアグラムの埋め込み |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 915dde5caf3eb930bdda3597aa7e0d2cdf1e8815
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546478"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Windows フォームでのダイアグラムの埋め込み
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows コントロールに表示される DSL 図を埋め込むことができます、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ウィンドウ。  
  
## <a name="embedding-a-diagram"></a>ダイアグラムの埋め込み  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Windows コントロールに DSL 図を埋め込むには  
  
1.  新しい追加**ユーザー コントロール**ファイルを DslPackage プロジェクト。  
  
2.  ユーザー コントロールをパネル コントロールを追加します。 このパネルにはは DSL 図が含まれます。  
  
     必要なその他のコントロールを追加します。  
  
     コントロールのアンカーのプロパティを設定します。  
  
3.  ソリューション エクスプ ローラーでユーザー コントロール ファイルを右クリックし、をクリックして**コードの表示**します。 コードには、このコンス トラクターと変数を追加します。  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  次の内容、DslPackage プロジェクトに新しいファイルを追加します。  
  
    ```  
    using System.Windows.Forms;  
    namespace Company.MyDSL  
    {  
      partial class MyDSLDocView  
      {  
        private UserControl1 container;  
        public override IWin32Window Window  
        {  
          get  
          {  
            if (container == null)  
            {  
              // Put our own form inside the DSL window:  
              container = new UserControl1(this,  
                (Control)base.Window);  
            }  
            return container;  
    } } } }  
  
    ```  
  
5.  DSL をテストするには、f5 キーを押して、サンプル モデル ファイルを開きます。 コントロール内に、ダイアグラムが表示されます。 ツールボックスとその他の機能が通常動作します。  
  
#### <a name="updating-the-form-using-store-events"></a>ストア イベントを使用してフォームを更新しています  
  
1.  フォーム デザイナーでは追加、 **ListBox**という`listBox1`します。 これにより、モデルに要素の一覧が表示されます。 モデルを使用して synchronism で保持*イベント格納*します。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)します。  
  
2.  カスタム コード ファイルでさらにメソッドをオーバーライド DocView クラス。  
  
    ```  
  
    partial class MyDSLDocView  
    {  
     /// <summary>  
     /// Register store event listeners.  
     /// This method is called when the model and diagram    
     /// have completed loading.   
     /// </summary>  
     protected override bool LoadView()  
      {  
        bool result = base.LoadView();  
        Store store = this.DocData.Store;  
        EventManagerDirectory emd = store.EventManagerDirectory;  
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));  
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));  
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));  
  
        // Do the initial parts list:  
        container.SetUpFormFromModel();  
        return result;  
      }  
     /// <summary>  
     /// Listener method called on creation of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void AddElement(object sender, ElementAddedEventArgs e)  
     {  
       container.Add(e.ModelElement as ExampleElement);  
     }  
     /// <summary>  
     /// Listener method called after deletion of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void RemoveElement(object sender, ElementDeletedEventArgs e)  
     {  
       container.Remove(e.ModelElement as ExampleElement);  
     }  
  
    ```  
  
3.  ユーザー コントロールの背後にあるコードでは、要素を追加および削除をリッスンするメソッドを挿入します。  
  
    ```  
  
          public partial class UserControl1 : UserControl { ...  
  
    private ExampleModel modelRoot;  
  
    internal void Add(ExampleElement e) { UpdatePartsList(); }  
    internal void Remove(ExampleElement e) { UpdatePartsList(); }  
  
    internal void SetUpFormFromModel()  
    {  
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;  
      UpdatePartsList();  
    }  
  
    private void UpdatePartsList()  
    {  
      StringBuilder builder = new StringBuilder();  
      listBox1.Items.Clear();  
      foreach (ExampleElement c in modelRoot.Elements)  
      {  
        listBox1.Items.Add(c.Name);  
      }  
    }  
  
    ```  
  
4.  DSL をテストするには、f5 キーを押しての実験用インスタンスで[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、サンプル モデル ファイルを開きます。  
  
     モデルでは、要素の一覧をリスト ボックスが表示されるが正しいことおよび取り消しとやり直しの任意の追加または削除後に注意してください。  
  
## <a name="see-also"></a>関連項目  
 [移動して、プログラム コードでモデルを更新しています](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)

