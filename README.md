# Cardiac-Disease-Diagnosis-Using-Large-Language-Models-in-Real-World-Medical-Scenarios
## 工作介绍
随着生成式大模型在自然语言处理领域的蓬勃发展，其在医学领域的潜力日益凸显。然而，现有研究多基于考试题或人工设计案例进行验证，缺乏真实患者数据的支撑。为此，本研究基于MIMIC-IV数据库，构建了包含4761名心脏疾病患者的子数据集——MIMIC-IV-Ext Cardiac Disease，涵盖了患者从入院到出院的各项检查结果及最终诊断。我们搭建了一个多轮交互框架，模拟医生指导患者进行院内检查的完整流程，并在此过程中评估大模型的主动思考与诊断能力。我们评估了GPT-4o、LLaMA3.1-70B和LLaMA3.1-8B模型在该框架下的表现，实验结果显示，大模型在心脏疾病诊断上具有一定潜力，但对标准医疗流程的遵循度不足，常出现漏诊及误诊等问题。此外，本研究提出了两阶段检索增强生成（RAG）策略，通过在模型诊断前与诊断过程中检索相似病例，为模型提供经验知识支持。实验证明，两阶段RAG策略可显著提升模型的诊断准确率及对检查流程的合理掌控，减少无效检查的次数。总体而言，本研究不仅验证了大模型在复杂医疗环境中进行诊断的可行性，也揭示了其潜在局限及改进方向，为利用真实临床数据优化大模型的诊断性能提供了新的思路与方法。

## 仓库介绍
在本仓库中我们提供了本工作的基本代码，包括构建数据集的代码以及多轮交互框架的代码，并提供了简单的应用实例。其中extract.py文件是构建数据集的代码，由于整个数据集的构建过程比较复杂，因此extract.py文件中的代码是分块保存的，每一块代码执行一项功能，依次运行这些代码块则可以实现整个数据集的构建过程。  

其余的代码则是整个多轮交互框架所使用的代码了。为了保证代码的可迁移性和通用性，整个多轮交互框架最终被封装成函数保存在model_chat.py文件中，multi_dialogue和multi_dialogue_RAG这两个函数分别是未加入和加入两阶段RAG策略的多轮交互框架主函数。其余函数为整个框架提供辅助。total_information_diagnose则实现了向模型提供患者全部检查结果这一过程。针对这三种情况我分别提供了针对Llama3.1-8b模型的示例代码以供参考。最后，evaluation.py文件是整个实验结束后的评估代码，由于评估内容较多，评估代码也按照分块的方式进行构建。template.py则是整个实验中用到的所有对话模板。

## 数据集
本工作的数据集以及两阶段交互框架所使用的RAG数据则会在近期被提交到 https://physionet.org/about/database/ 网站上供大家使用。
