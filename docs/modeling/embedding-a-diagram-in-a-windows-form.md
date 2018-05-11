---
title: Windows フォームでのダイアグラムの埋め込み
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: db011f9842d00b6a39be3f1e9f4d4d7a090f2581
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Windows フォームでのダイアグラムの埋め込み
表示されます、Windows のコントロールに DSL 図を埋め込むことができます、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ウィンドウです。

## <a name="embedding-a-diagram"></a>ダイアグラムの埋め込み

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Windows コントロールでの DSL 図を埋め込むには

1.  新しい**ユーザー コントロール**DslPackage プロジェクトへのファイルです。

2.  ユーザー コントロール パネル コントロールを追加します。 このパネルは、DSL 図が含まれます。

     必要なその他のコントロールを追加します。

     コントロールのアンカー プロパティを設定します。

3.  ソリューション エクスプ ローラーで、ユーザー コントロール ファイルを右クリックし、をクリックして**コードの表示**です。 コードにこのコンス トラクターと変数を追加します。

    ```csharp

    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;

    ```

4.  次のコンテンツを含む、DslPackage プロジェクトに新しいファイルを追加します。

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

5.  DSL をテストするには、f5 キーを押して、サンプル モデル ファイルを開きます。 コントロール内に、ダイアグラムが表示されます。 ツールボックスおよびその他の機能が通常動作します。

#### <a name="updating-the-form-using-store-events"></a>ストアのイベントを使用してフォームの更新

1.  フォーム デザイナーでは追加、 **ListBox**という`listBox1`です。 これにより、モデルに要素の一覧が表示されます。 使用して、モデルと synchronism で保持される*イベント格納*です。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)です。

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

3.  コードでは、ユーザー コントロールの内側に、要素を追加および削除をリッスンするメソッドを挿入します。

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

4.  DSL をテストするには、f5 キーを押して、実験用インスタンスの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、サンプル モデル ファイルを開きます。

     リスト ボックスでは、モデルでは、要素の一覧が表示およびが正しいことおよび元に戻す/やり直しの任意の追加または削除後に注意してください。

## <a name="see-also"></a>関連項目

- [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)
