---
title: 'チュートリアル: エディター拡張機能とショートカット キーの使用 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d009351efdd36e0d415d0e2e457f7974608ab665
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886501"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>チュートリアル: エディター拡張機能とショートカット キーを使用します。
エディター拡張機能で、ショートカット キーに応答することができます。 次のチュートリアルでは、テキスト ビューにショートカット キーを使用してビューの表示要素を追加する方法を示します。 このチュートリアルは、ビューポート adornment エディター テンプレートに基づいており、使用して、表示要素を追加することができます、+ 文字。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールしないでください。 Visual Studio のセットアップのオプション機能として含まれています。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) プロジェクトを作成します。  
  
1. C# VSIX プロジェクトを作成します。 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/機能拡張**、し**VSIX プロジェクト**)。ソリューション `KeyBindingTest`の名前を指定します。  
  
2. エディターのテキストの表示要素の項目テンプレートをプロジェクトに追加し、名前`KeyBindingTest`します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
3. 次の参照を追加し、設定**CopyLocal**に`false`:  
  
    Microsoft.VisualStudio.Editor  
  
    Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft.VisualStudio.Shell.14.0  
  
    Microsoft.VisualStudio.TextManager.Interop  
  
   KeyBindingTest クラス ファイルでは、PurpleCornerBox にクラス名を変更します。 左余白に表示される電球を使用して、他の適切な変更を行います。 コンス トラクター内から装飾層の名前を変更する**KeyBindingTest**に**PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  

KeyBindingTestTextViewCreationListener.cs クラス ファイルでから AdornmentLayer の名前を変更する**KeyBindingTest**に**PurpleCornerBox**:
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  

## <a name="handle-typechar-command"></a>TYPECHAR コマンドを処理します。
Visual Studio 2017 バージョン 15.6 のエディターの拡張機能でのコマンドを処理する唯一の方法を実装する前に、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>ベースのコマンドのフィルター。 Visual Studio 2017 バージョン 15.6 では、エディター コマンド ハンドラーに基づいた最新の簡略化されたアプローチが導入されました。 次の 2 つのセクションでは、旧バージョンと最新のアプローチの両方を使用してコマンドを処理する方法を示します。

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>(Visual Studio 2017 バージョン 15.6) より前のコマンドのフィルターを定義します。

 コマンドのフィルターの実装は、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>、表示要素をインスタンス化して、コマンドを処理します。  
  
1.  クラス ファイルを追加し、その名前を `KeyBindingCommandFilter`にします。  
  
2.  次の using ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3.  KeyBindingCommandFilter という名前のクラスを継承する必要があります<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>します。  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4.  コマンドのチェーン、およびコマンド フィルターが既に追加されているかどうかを表すフラグで、テキスト ビューのプライベート フィールドを次のコマンドを追加します。  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5.  テキスト ビューを設定するコンス トラクターを追加します。  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6.  実装、`QueryStatus()`メソッドとして、次のとおりです。  
  
    ```csharp  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7.  実装、`Exec()`ためプラス記号の場合、ビューに追加します紫色のボックスをその it メソッド (**+**) 文字を入力します。  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>(Visual Studio 2017 バージョン 15.6) より前のコマンドのフィルターを追加します。
 Adornment プロバイダーは、テキスト ビューにコマンド フィルターを追加する必要があります。 この例で、プロバイダーを実装して<xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>テキスト ビューの作成イベントをリッスンするようにします。 この表示要素のプロバイダーには、表示要素の Z オーダーを定義する装飾層もエクスポートされます。  
  
1.  次の追加、KeyBindingTestTextViewCreationListener ファイルでステートメントを使用します。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2.  テキスト ビュー アダプターを取得するには、インポートする必要があります、<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>します。  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
3.  変更、<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>メソッドを追加するため、`KeyBindingCommandFilter`します。  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
4.  `AddCommandFilter`ハンドラーがテキスト ビュー アダプターを取得し、コマンドのフィルターを追加します。  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>(Visual Studio 2017 バージョン 15.6 以降) のコマンド ハンドラーを実装します。

最初、最新のエディターの API を参照するプロジェクトの Nuget 参照を更新します。

1. クリックし、プロジェクトを右クリックして**Nuget パッケージの管理**します。

2. **Nuget パッケージ マネージャー**を選択します、**更新** タブで、、**すべてのパッケージを選択します**チェック ボックスをオンし、**更新**します。

コマンド ハンドラーの実装は、 <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>、表示要素をインスタンス化して、コマンドを処理します。  
  
1. クラス ファイルを追加し、その名前を `KeyBindingCommandHandler`にします。  
  
2. 次の using ステートメントを追加します。  
  
   ```csharp  
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;   
   ```  
  
3. KeyBindingCommandHandler という名前のクラスを継承する必要があります`ICommandHandler<TypeCharCommandArgs>`、としてエクスポート<xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:
  
   ```csharp  
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>  
   ```  
  
4. コマンド ハンドラーの表示名を追加します。  
  
   ```csharp  
   public string DisplayName => "KeyBindingTest";
   ```  
    
5. 実装、`GetCommandState()`メソッドとして、次のとおりです。 このコマンド ハンドラーは、コア エディター TYPECHAR コマンドを処理するため、コア エディターにコマンドを有効にするを委任することができます。
  
   ```csharp  
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   } 
   ```  
  
6. 実装、`ExecuteCommand()`ためプラス記号の場合、ビューに追加します紫色のボックスをその it メソッド (**+**) 文字を入力します。 
  
   ```csharp  
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```  
   7. 装飾層の定義をコピー *KeyBindingTestTextViewCreationListener.cs*ファイルを*KeyBindingCommandHandler.cs*し削除*KeyBindingTestTextViewCreationListener.cs*ファイル。
 
   ```csharp  
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;    
   ```  

## <a name="make-the-adornment-appear-on-every-line"></a>すべての行に表示される表示要素を作成します。  

すべての文字で表示されていた元の表示要素の ' a' のテキスト ファイル。 応答の表示要素を追加するコードを変更しましたところ、 **+** 文字、行にのみ表示要素を追加します場所、 **+** 文字を入力します。 1 回以上表示要素が表示されるように、表示要素のコードを変更できますすべて 'a'。  
  
*KeyBindingTest.cs*ファイルで、変更、 `CreateVisuals()` 'a' 文字の装飾にビュー内のすべての行を反復処理するメソッド。  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="build-and-test-the-code"></a>ビルドし、コードのテスト  
  
1.  KeyBindingTest ソリューションをビルドし、実験用インスタンスで実行します。  
  
2.  作成するか、テキスト ファイルを開きます。 入力文字を含む一部の単語 'a' と入力し、 **+** テキスト ビューで任意の場所。  
  
     紫色の四角形は、ファイル内のすべての 'a' 文字に表示する必要があります。
