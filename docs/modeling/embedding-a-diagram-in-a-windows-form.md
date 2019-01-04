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
ms.openlocfilehash: 41279e483e2ea752fd6cb573d7632f61a206003d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841756"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Windows フォームにダイアグラムを埋め込む

DSL 図は、Visual Studio ウィンドウに表示される、Windows のコントロールで埋め込むことができます。

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Windows コントロールに DSL ダイアグラムを埋め込む

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
    private MyDSLDocView docView;
    ```

4.  次の内容、DslPackage プロジェクトに新しいファイルを追加します。

    ```csharp
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

5.  DSL をテストするには、キーを押して**F5**サンプル モデル ファイルを開くとします。 コントロール内に、ダイアグラムが表示されます。 ツールボックスとその他の機能が通常動作します。

## <a name="update-the-form-using-store-events"></a>ストア イベントを使用してフォームを更新します。

1.  フォーム デザイナーでは追加、 **ListBox**という`listBox1`します。 これにより、モデルに要素の一覧が表示されます。 使用して、モデルと同期されている*イベント格納*します。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)します。

2.  カスタム コード ファイルでさらにメソッドをオーバーライド DocView クラス。

    ```csharp
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

    ```csharp
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

4.  DSL をテストするには、キーを押して**F5** Visual Studio の実験用インスタンスのサンプル モデル ファイルを開くとします。

     モデルでは、要素の一覧をリスト ボックスが表示されるが正しいことおよび取り消しとやり直しの任意の追加または削除後に注意してください。

## <a name="see-also"></a>関連項目

- [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)
