# Metodos unit testing

[SetUp]
public void Setup()
{
}

[OneTimeSetUp]
public void Setup()
{	
}

[TearDown]
public void TearDown()
{
}


# Multiples casos de uso

[Test]
[TestCase("unittest")]
[TestCase("")]
public void Test_method(object parameter)
{
}

[Test]
[TestCase(DMUA.Enums.OptimizerJobTypes.Proposal)]
[TestCase(DMUA.Enums.OptimizerJobTypes.Mobility)]
public async Task GetPreStageData_SettingIsOk_SetPreStageData(string optimizerJobType)


# Asegurar que un metodo se ejecuta sin arrojar una excepción.
Assert.DoesNotThrow(() => _allocatePreProcessUtility.CheckSettingRequestAllocationAsync(setting, CancellationToken.None));

# Asegurar que algún método se ejecute
Mock.Assert(() => _optimizerServiceProxy.RunOptimizerProcessAsync(Arg.AnyString, Arg.AnyString, Arg.IsAny<DMUA.RequestAllocationSettingDto>(), Arg.IsAny<IUnitAllocatorDomainService>(), _cancellationToken), Occurs.Once());


# Castear un result 

Assert.IsNotNull(result);
Assert.IsInstanceOf<OkObjectResult>(result);
var requestResult = (OkObjectResult)result;
Assert.AreEqual(jobId, ((RequestAllocationJobStatusDto)requestResult.Value).JobId);
var requestAllocation = (RequestAllocationJobStatusDto)requestResult.Value;
Assert.That(!string.IsNullOrEmpty(requestAllocation.UserName));


# Mockear un método asincronico

Mock.Arrange(() => _optimizerService.GenerateNewJobIdAsync(Arg.IsAny<UnitAllocatorScenarioDto>(), Arg.AnyString, Arg.IsAny<Nullable<int>>(), Arg.AnyInt, CancellationToken.None, Arg.AnyString)).Returns(Task.FromResult(1));
